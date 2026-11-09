---
name: code-review
description: Review code changes for bugs, security holes and regressions before they merge. Use when the user says "review my changes", "review this PR", "check this diff", "is this safe to merge", or names a branch, commit or files to look over.
---

# Code review

The goal is a short list of real problems, each one verified against the code. A review with two true findings beats one with ten guesses.

## 1. Get the exact change

- Working tree: `git status` first, then `git diff HEAD` (staged + unstaged). Untracked files do not show in a diff: read them.
- Branch: find the base, do not assume `main`. Use `git symbolic-ref refs/remotes/origin/HEAD` or ask. Diff with `git diff <base>...HEAD` (three dots = since the merge base).
- PR number: `gh pr diff <n>` if `gh` is available; otherwise ask for the branch.
- If the diff is over ~1500 lines, say so and review the riskiest files first (auth, payments, data writes, migrations, concurrency), listing what you skipped.

## 2. Understand intent

Read the commit messages or PR text. A bug is a gap between what the change is meant to do and what it does. If the intent is unclear, state your assumption.

## 3. Read beyond the hunk

For every changed function, open the full function and the code it calls. For every changed signature, return type, default value, config key or DB column, search for all usages (`git grep -n <name>`) and check each caller still works. Most real bugs live in code the diff did not touch.

## 4. Look for these, in this order

1. Wrong behavior: inverted conditions, wrong variable, missing `await`, early return skipping cleanup, error swallowed, partial writes without a transaction.
2. Security: untrusted input reaching SQL, shell, HTML, file paths, redirects or deserialization; missing authorization on a new route (auth is not the same as ownership); secrets or tokens in code or logs.
3. Data and compatibility: migrations that lock or drop data, removed fields still read by clients, changed API response shape, cache keys that now collide.
4. Missing tests for the changed behavior.

Skip what a linter, formatter or type checker already catches, unless the project has none.

## 5. Verify before reporting

For each candidate finding, confirm it by reading the code path that triggers it. If you can run the tests or a quick script to prove it, do. If you still are not sure, either drop it or list it under "Questions", never as a bug.

## Output

Group by severity:
- **Blocker**: will break production, lose data or open a security hole.
- **Should fix**: real bug in a less common path, or a missing test for risky logic.
- **Nit**: only if it costs the reader nothing; max 3.

Each finding:
```
path/to/file.ts:42 - <what is wrong, one sentence>
Scenario: with <input/state>, <what happens> instead of <expected>.
Fix: <smallest change, a code snippet if under 5 lines>
```

End with "Questions" (things you could not verify) and a one-line verdict: merge, merge after fixes, or rework.

## Do not

- Edit files during a review unless the user asks for fixes.
- Pad the list. If you find nothing, say "No bugs found" and what you checked.
- Restate what the diff does line by line.
- Report a problem in unchanged code as part of this change; mention it separately if it is serious.
