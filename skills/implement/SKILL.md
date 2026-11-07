---
name: implement
description: "Implement a piece of work based on a spec or set of tickets."
disable-model-invocation: true
---

Implement the work described by the user in the spec or tickets.

Read the ticket, its linked spec and blockers, `GLOSSARY.md`, and the ADRs in `docs/adr/`, where present.

Use `tdd` for behavior changes and bug fixes at pre-agreed seams.

Run typechecking regularly, single test files regularly, and the full test suite once at the end.

Once done, call the Skill tool with "code-review" to review the work.

For local tickets, start only when every blocker is `done`. Set Status to `in-progress` before implementation. After verification and code review pass, check the verified acceptance criteria and set Status to `done`. Record any remaining blockers or incomplete work in the ticket.

Commit your work to the current branch using commit-msg to generate the message.
