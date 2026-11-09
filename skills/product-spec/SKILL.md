---
name: product-spec
description: Write a product requirements document (PRD) or feature spec. Use when the user describes a feature or product idea and asks for a spec, PRD, requirements, user stories, "scope this", or something to hand to engineers or designers.
---

# Product spec

## 1. Clarify (max 3 questions, only if the answer changes the spec)
Who has the problem, what triggers it, and what "done" looks like. If the user wants a draft now, proceed and mark guesses as assumptions.

## 2. Separate facts from assumptions
Everything the user told you or that is in provided docs is a fact. Everything else is `(assumption)`. Never invent user research, quotes, usage numbers, revenue impact or baselines. A metric without a known baseline says "baseline: to measure".

## 3. Write one page

**Problem**: who has it, when, what it costs them today (time, money, errors). Evidence only if provided.

**Users**: primary user and the job they are trying to get done. Secondary users only if they act in the flow (admin, approver).

**Solution (smallest version that solves the problem)**: user stories, "As a <user>, I can <action> so that <outcome>." 3-7 stories. Each story has acceptance criteria:
- Given <state>, when <action>, then <observable result>.

**Edge cases**: empty states, errors, permissions (who cannot do this), limits (large inputs, many items), concurrent edits, undo/delete, existing data migration.

**Non-functional**: only those that matter here: performance target, privacy/personal data, security, accessibility, localisation, analytics events to track.

**Out of scope**: mandatory. What this version will not do, including obvious next features.

**Success metric**: one primary metric, target, time window, how it is measured. One guardrail metric that must not get worse.

**Dependencies and risks**: other teams, APIs, legal, data needed.

**Open questions**: each with a suggested owner.

**Rough plan**: milestones in order (e.g. internal beta -> 10% rollout -> GA). Dates only if the user gave a deadline.

## Rules
- Describe behaviour, not implementation, unless the user asks for technical design.
- No feature without a problem behind it; if one appears, move it to Out of scope or Open questions.
- Plain language, no "seamless", "robust", "leverage".
- If the idea does not hold up (no clear user, problem already solved by an existing feature), say so before writing the spec.
