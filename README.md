# Agent skills

Personal standalone agent skills, shared across computers through Git.
The checkout lives at `~/.agents`, so Codex discovers the skills directly in
`~/.agents/skills`. There is no separate installation or copy step after pulling.

## Set up another computer

Install Git, authenticate with GitHub, and install Codex. Then clone this repo.

Windows (PowerShell):

```powershell
git clone https://github.com/Pablo-Goros/agent-skills.git "$env:USERPROFILE\.agents"
```

macOS or Linux:

```sh
git clone https://github.com/Pablo-Goros/agent-skills.git "$HOME/.agents"
```

The destination must be absent or empty. If `.agents` already contains files,
back it up outside that directory first, clone the repo, then compare and bring
over any local skills you want to keep. Commit and push those additions so the
other computers receive them too.

Open Codex and check the available skills. Codex detects skill changes
automatically; restart it if a skill or update does not appear.

## Receive updates

Run this on each computer before using or editing the skills:

```sh
cd ~/.agents
git pull --ff-only
```

In PowerShell, `cd "$env:USERPROFILE\.agents"` selects the same location.
Git does not synchronize automatically. Pulling downloads changes already
committed and pushed from another computer. No scheduled synchronization is
configured by this repository.

If a pull fails, run `git status`. Preserve any local edits by committing them or
stashing them before retrying. If the branches have diverged, reconcile them
explicitly; do not force-push or discard changes to make synchronization pass.

## Edit and share skills

Pull first, edit the files directly in `skills/`, then review and publish:

```sh
git diff
git status --short
git add skills
git commit -m "docs: improve skill instructions"
git push
```

If you change the repository documentation or configuration, stage those files
explicitly too. On every other computer, use `git pull --ff-only` to receive the
changes. Prefer finishing and pushing edits on one computer before editing the
same skill on another.

## Repository layout

```text
skills/
  skill-name/
    SKILL.md          # Instructions, with name and description in YAML front matter
    agents/           # Optional UI metadata
    references/       # Optional supporting documentation
    scripts/          # Optional executable helpers
    assets/           # Optional templates and other resources
```

Keep each skill's complete folder, including any supporting files stored beside
`SKILL.md`. Use relative links within a skill and home-relative paths in commands
instead of paths tied to a particular username or computer. Keep skill names
unique across your installed skills.

This repository includes the standalone `codebase` and `concept` skills migrated
from `~/.codex/skills`. Edit their copies here going forward. Avoid reinstalling
duplicate copies in the old location.

## Scope and dependencies

- This repo tracks personal standalone skills and their supporting files.
- Codex supplies bundled system skills, including `skill-creator` and
  `skill-installer`; they are not copied here.
- Install the plugins you use through Codex on each computer. Plugin caches,
  credentials, account connections, and tool availability are managed separately.
  Copying skill instructions does not install the tools they describe.
- Some skills create or run Bash scripts. Install the required runtime and tools
  on each computer when using those workflows.
- Preserve existing attribution and license files for third-party content. A pull
  from this repo distributes the versions checked in here; it does not fetch
  updates from the skills' original authors. Review and incorporate upstream
  updates here, then commit and push them once.
- Keep secrets and machine-specific configuration outside this repository.

## Codex documentation

See the [official skill documentation](https://learn.chatgpt.com/docs/build-skills)
for skill structure, local discovery, and plugin distribution.
