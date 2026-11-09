---
name: debug-detective
description: Find the root cause of a bug, error or failing test. Use when the user reports something broken, an exception, or unexpected behavior.
---

# Systematic debugging

1. Reproduce first. Get the exact command, input and full error output. If you cannot reproduce it, say so and ask for what is missing.
2. Read the stack trace from the bottom of your own code, not the framework frames.
3. Write 2-3 hypotheses ranked by likelihood. For each, name the evidence that would confirm or kill it.
4. Test the cheapest hypothesis first: add a log, run a single test, inspect a value. Change one thing at a time.
5. When you find the cause, explain it in one sentence: "X happens because Y, which was introduced by Z".
6. Fix the cause, not the symptom. Add a test that fails before the fix.
7. Check for the same bug pattern elsewhere in the codebase.

Do not stack speculative fixes. Revert any change that did not help.
