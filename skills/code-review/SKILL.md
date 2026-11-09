---
name: code-review
description: Review a diff or a set of files for correctness bugs, security issues and risky changes. Use when the user asks to review code, a PR, a branch or "my changes".
---

# Code review

1. Get the change: run `git diff` (or `git diff main...HEAD` for a branch). If the user named files, read them in full, not just the hunks.
2. For each changed function, ask: what input breaks this? Check null/empty values, off-by-one, error paths, concurrency, time zones, and unhandled promise rejections.
3. Check security: user input reaching SQL, shell, HTML or file paths; secrets in code; missing auth checks on new endpoints.
4. Check what the change does NOT touch: callers of a changed signature, tests that should change, migrations, docs.

## Report

List findings from most to least severe. For each one:
- file:line
- one sentence: what is wrong
- a concrete scenario: "with input X, Y happens instead of Z"
- the smallest fix

Skip pure style opinions unless they hide a bug. If nothing is wrong, say so plainly. Never invent a finding to have something to say.
