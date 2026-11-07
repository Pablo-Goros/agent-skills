---
name: implement-spec
description: "Implement the result of /to-spec and /to-tickets in code."
disable-model-invocation: true
---

You have been provided a spec. This spec should have tickets associated with it, describing how to implement the spec.

Read the supplied spec, its sibling `tickets/` directory, `GLOSSARY.md`, and the ADRs in `docs/adr/`, where present.

Implement the entire spec on one integration branch. The coordinator manages ticket statuses: `in-progress` before dispatch and `done` after successful verification and integration.

The tickets are not a list of steps. They are a **task graph** with blocking relationships between them. This means there is always a **frontier** of tickets which are ready to be grabbed.

Communication to and from subagents should be sparse. Communicate primarily through **context pointers**: to the spec, tickets, research notes, and previous commits. Don't duplicate information already available via pointers.

**Implementer subagents** should be run in the background where possible for maximum concurrency.

## Steps

1. Read the spec and tickets to understand the task graph.

2. (optional) Use an **exploration subagent** to conduct any exploration required by the tickets - relevant codebase files or external documentation. Ensure the exploration subagent can save files - it should save its markdown notes in a directory outside the repo, accessible by all future subagents. This lets **implementer subagents** focus on implementation rather than exploration.

3. Create the integration branch. If the user requests a PR, open a draft after the first merge in step 5 and reference the local spec and tickets.

4. Use **implementer subagents** to implement each ticket, each in its own worktree on its own branch. Each implementer subagent:
   - confirms its worktree is based on the integration branch before starting, and resets onto it if not;
   - uses `tdd` to implement its ticket;
   - merges the integration branch tip into its own branch;
   - verifies the ticket's acceptance criteria and runs the necessary checks before reporting done.

5. Once an **implementer subagent** completes, merge its work to the integration branch with a **merger subagent**, which verifies the integrated result.

   If integration exposes a problem, send a focused description back to the implementer for a fix. The ticket remains `in-progress`.

   After successful integration and verification, the coordinator checks the verified acceptance criteria in the ticket and sets its Status to `done`.

6. If this changes the **frontier** of available tickets, kick off more **implementer subagents** to work on the new tickets. This allows for maximum concurrency.

7. Once all tickets are complete, call the Skill tool with `code-review` on the integration branch. Fix all issues raised by the code review in a single **implementer subagent**.

8. Confirm every ticket is `done` and its acceptance criteria remain satisfied after final review fixes. If a draft PR exists, mark it ready for review. Report the integration branch and any unresolved work.

9. Clean up all **implementer subagent** worktrees.
