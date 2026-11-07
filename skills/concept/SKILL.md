---
name: concept
description: Teach a general software engineering, architecture, framework, or tooling concept without investigating the current repository. Use for standalone questions about what a technology or pattern is, how it works, why it exists, what problem it solves, or how it compares with alternatives. Read-only; do not implement changes.
---

# Concept

Teach the requested concept clearly without inspecting the repository by default.

## Workflow

1. Identify the user's likely familiarity and the central question: what it is, how it works, why it exists, or how it compares.
2. Give the direct explanation in plain language.
3. Introduce technical terminology progressively, defining terms before relying on them.
4. Use a small concrete example, analogy, or comparison when it materially improves understanding.
5. Consult official primary documentation only when current, version-specific, or otherwise unstable details matter.

## Answering Guidelines

- Keep the explanation repository-agnostic unless the user asks how the current project uses the concept.
- If repository inspection is required, route the question to `$codebase`; mixed conceptual and project-specific questions also belong to `$codebase`.
- Distinguish a simplified mental model from precise technical behavior when both are useful.
- Explain tradeoffs without turning the answer into an implementation proposal or technology recommendation unless requested.
- State uncertainty explicitly and avoid presenting conventions as universal rules.
- Do not inspect or edit project files, start services, or otherwise mutate state unless separately requested.

Use the lightest response structure that fits: direct explanation, how it works, why it matters, and an optional example or comparison.
