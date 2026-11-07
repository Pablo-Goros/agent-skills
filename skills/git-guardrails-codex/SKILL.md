---
name: git-guardrails-codex
description: Set up Codex command rules to restrict git push and destructive Git operations. Use when configuring Git guardrails for Codex, customizing blocked commands, or verifying existing rules.
---

# Git guardrails for Codex

Configure native Codex execution rules using [assets/git-guardrails.rules](assets/git-guardrails.rules). No Claude Code hooks, Bash, or jq are required.

## Scope and enforcement

Use the scope already specified by the user. Otherwise ask whether installation should cover this repository or all projects. Editing this reusable skill alone does not authorize installing active rules.

- User: `$CODEX_HOME/rules/git-guardrails.rules`, defaulting to `~/.codex/rules/git-guardrails.rules`.
- Project: `<repo>/.codex/rules/git-guardrails.rules`; its project config layer must be trusted.

Inspect the installed Codex version and `codex execpolicy check --help`. Consult the [official rules documentation](https://learn.chatgpt.com/docs/agent-configuration/rules) when compatibility is uncertain.

Documented rules control commands outside the sandbox. They are not a universal Git interceptor. Do not promise enforcement in full-access or sandbox-disabled sessions without verifying client behavior. AGENTS.md instructions can supplement rules but are not enforcement.

The defaults forbid direct push, reset, clean, checkout, restore, and common forced branch deletion forms. Entire reset/clean/checkout/restore subcommands are restricted because prefix rules cannot inspect arbitrary later flags. This also restricts benign checkout operations; `git switch` remains available. The branch rule also restricts ordinary `--delete`.

Rules match argument prefixes. Git global options before subcommands (`git -C repo push`), aliases, alternate executable paths, reordered branch flags, scripts, and shell wrappers need separate evaluation. Do not claim the defaults cover them.

## Install or customize

1. Read existing rules at the selected scope. Preserve unrelated configuration. Copy the bundled asset to the dedicated target file; merge requested changes if that file already contains user customizations. Avoid overwriting `default.rules`.
2. Honor requested customization. Use `forbidden` for blocked commands; use `prompt` only when the user requests per-invocation approval. Add prefixes for alternate Git executable names or paths actually used in the environment. Avoid broad allow rules.
3. Test Git global options and shell wrappers used by this client. Report unmatched dangerous examples as coverage gaps. Restrict broader prefixes only when that tradeoff is within the requested scope; do not invent wildcard syntax.
4. Restart Codex to load the rules. Change sandbox or approval settings only when requested.

## Verify and report

Policy checks inspect tokens without executing Git:

```powershell
codex execpolicy check --pretty --rules <target-file> -- git push origin main
codex execpolicy check --pretty --rules <target-file> -- git reset --hard HEAD
codex execpolicy check --pretty --rules <target-file> -- git status
```

Check every restricted category and benign status, diff, add, commit, and switch examples. Require JSON `decision: forbidden` for restricted examples and no matching forbidden rule for benign examples. An unmatched result is not an explicit allow. Include relevant existing rule files using repeated `--rules` flags to assess combined policy.

Evaluate executable paths, Git global options, and the actual shell invocation form used by the client. Never test by executing destructive commands or pushing. Policy checks establish matching, not runtime enforcement. Report installed paths, customizations, check results, coverage gaps, and any pending restart or runtime verification.
