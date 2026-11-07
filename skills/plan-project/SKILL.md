---
name: plan-project
description: Plan a huge chunk of work (more than one agent session can hold) as a shared map of decision tickets on your issue tracker, and resolve them one at a time until the way to the destination is clear.
disable-model-invocation: true
---

## Scope

Shape the overall project: what it should accomplish, its major capabilities, and how the system fits together.

Start from an idea, assignment, or existing project context. Establish project-level requirements and architecture; deepen individual features only where needed to make those decisions.

Specs, tickets, and implementation require a separate request.

## Interviewing

**Interviewing:** Conversation with the user. Use `ask-user` and `domain-modeling` when requirements or design choices need clarification. Read the available context first; ask only unresolved questions. Interviewing can happen throughout planning.

## Documents

- `docs/project.md`: business purpose, intended users, main functionalities, scope, constraints, and success criteria. For assignments, include required deliverables and evaluation criteria, linking to the source.
- `docs/architecture.md`: a short technical overview of components, responsibilities, data ownership, flows, and integrations. Include diagrams where helpful.
- `docs/adr/`: significant architectural decisions and their rationale, following domain-modeling's ADR criteria.
- `GLOSSARY.md`: agreed domain terminology, updated when needed.

Reuse existing documents. Keep detailed feature behavior in feature specs and architectural rationale in ADRs, linking to them from the overviews.

## Decision map

Create `docs/decision-map.md` when planning spans sessions or involves dependent decisions. Keep it a short index with these sections:

- Destination: what this planning effort should establish.
- Open decisions: precise questions and their dependencies, including questions currently blocked by other decisions.
- Decisions so far: a brief outcome and link to the document containing the answer.
- Not yet specified: relevant areas that are not yet clear enough to formulate as precise questions.
- Out of scope: links to relevant scope exclusions in `docs/project.md`.

When a decision is resolved, record its answer in the appropriate project document and move its map entry from Open decisions to Decisions so far.

As understanding develops, turn newly clarified areas into open decisions. Keep the map current without duplicating detailed rationale.

## Process

1. Understand the idea or assignment, existing context, constraints, and unknowns.
2. Establish the project overview: purpose, users, main functionalities, scope, constraints, and success criteria.
3. Plan the architecture: boundaries, data ownership, integrations, deployment, and relevant quality requirements. Compare meaningful alternatives.
4. Record agreed outcomes in the project documents, qualifying ADRs, and glossary. Update the decision map when present.

Interview throughout as needed. Use research or prototypes to resolve uncertainty. Revisit scope when architectural discoveries affect it.

Across sessions, resume from existing documents and unresolved decisions.

Finish when the agreed scope and architecture are clear enough to proceed, with remaining questions explicitly deferred or blocking.
