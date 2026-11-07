---
name: commit-msg
description: Suggest a concise English Conventional Commit message from Git changes or a supplied change description. Use when the user requests a commit message suggestion or invokes $commit-msg.
---

# Commit message suggestion

Generate one commit message suggestion that accurately summarizes the changes.

When the user supplies a diff or change description, use it. Otherwise inspect the current repository with read-only Git commands: check status and use the staged diff when staged changes exist; otherwise use the working tree diff and inspect relevant untracked files. If there are no changes or insufficient context, ask briefly for the changes to summarize.

Follow these rules:

- Use the Conventional Commit format `<action>: <short description>`.
- Choose the lowercase type that best describes the changes, such as `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, or `revert`.
- Never add a scope, topic, or field in parentheses or brackets after the action. Use `feat: add login`, never `feat(login): add login`.
- Write the description in English as one concise phrase on one logical line. Prefer imperative wording, such as `add`, `fix`, or `update`.
- Return only the single-line message, with no body, footer, explanation, list, quotation marks, or Markdown fence.
- Suggest the message only; do not stage files or create a commit unless separately requested.

Examples:

`feat: add password reset`

`fix: handle empty search results`

`refactor: simplify configuration loading`
