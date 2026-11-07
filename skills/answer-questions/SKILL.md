---
name: answer-questions
description: Answer lists of questions using stable numbered headings, including follow-ups to earlier numbered answers. Use only when the user explicitly invokes this skill by name (for example, `$answer-questions`).
---

# Numbered Questions and Answers

Answer every question in the user's message in a single response, in the order given. Do not omit an item or defer it to a later reply.

## Numbered question lists

- Preserve the user's original question numbers. If the list is unnumbered, assign consecutive numbers in its original order.
- Put each complete question directly above its answer, using exactly this pattern:

  ```text
  1. Full question text

  Answer
  ```

- Do not add a generic introduction, progress tracking, or repetitive preamble unless the user asks for one.

## Follow-ups

For a follow-up to a prior answer, retain the number of the question it concerns. Use the user's new follow-up wording as the heading, rather than restating the original question or allocating a new number. Give a focused answer to that follow-up and avoid repeating prior material unnecessarily.

When several follow-ups appear in one message, answer all of them in that response with their corresponding original numbers and follow-up wording. Infer the referenced number from context when it is clear; if it is genuinely ambiguous, ask one brief clarification rather than guessing.

Treat an explicitly new list of questions as a fresh set, with numbering taken from that list or assigned anew if it has none.

## Language and tone

Answer in the user's language. Be clear and direct, and match the requested level of detail.
