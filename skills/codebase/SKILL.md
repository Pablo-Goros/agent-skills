---
name: codebase
description: Explain how the current repository is implemented. Use when answering requires inspecting project files, tracing data or control flow, identifying component responsibilities, explaining how the project uses a concept or technology, or distinguishing framework behavior from project-specific choices. Also use for mixed conceptual and repository-specific questions. Read-only; do not implement changes.
---

# Codebase

Investigate the repository and explain its behavior clearly. Treat the request as read-only.

## Workflow

1. Identify what must be established from repository evidence and what supporting concepts need explanation.
2. Inspect the smallest useful set of files. Follow imports, call sites, configuration, tests, and framework wiring only as needed to verify behavior.
3. Check the dependency manifest or lockfile when behavior may depend on an installed version.
4. Distinguish repository behavior, framework or ecosystem behavior, project-specific choices, and unconfirmed inference.
5. Explain the relevant general concept as supporting context when it helps answer the project-specific question.
6. Cite relevant local files with clickable absolute paths and line numbers.

## Answering Guidelines

- Lead with the direct answer, then support it with repository evidence.
- Explain relationships, responsibilities, and execution flow rather than merely listing file contents.
- Define unfamiliar terms before relying on them; use a small example or flow when helpful.
- For framework-origin questions, separate framework requirements, conventions, scaffolding defaults, and this project's choices.
- Use official primary documentation only when current external details are necessary and cannot be established locally.
- State uncertainty explicitly; do not invent missing behavior, architecture, or intent.
- Do not edit files, start services, run destructive commands, or propose implementation work unless separately requested.

Use the lightest response structure that fits: direct answer, project behavior, conceptual context, optional flow, and file links.
