---
name: search-skill
description: Find the right skill or sequence of skills for what you want to do.
disable-model-invocation: true
argument-hint: "What you need to do, including any possible next steps"
---

Help the user choose skills for their intended work.

The user may describe one task, several related tasks, or an
uncertain sequence.

## Find the fit

Identify the intended outcome, what material the user already
has, and which later steps are tentative. Use the conversation
to fill gaps. Ask a focused question only when its answer would
change the recommendation.

Discover candidates from the session's skill catalog and the
available skill directories. Treat descriptions as pointers:
read each candidate's SKILL.md before recommending it or
describing its behavior.

Base recommendations on the current instructions. Verify
dependencies or companion skills when the proposed route
relies on them.

## Recommend a route

Recommend the smallest set of skills that covers the request.

Lead with the skill to use now and explain why it fits.
For multiple steps, show their order and what passes from
one to the next. Keep “maybe Y” conditional: explain when
that next skill becomes useful.

Distinguish alternatives only when the choice matters.
Mention consequential behavior—such as committing changes
or modifying external systems—when it affects the choice.

Use exact invocation names, such as `$workflow-builder`.
Give a suggested starting prompt when it would help.

If part of the request has no suitable available skill,
identify the gap plainly.

## Scope

The output is a recommendation. Leave invocation and execution
of the recommended skills to the user.
