---
name: pr-description
description: Write a pull request title and description for the current branch. Use when the user asks to open a PR or describe their changes.
---

# Pull request description

1. Compare with the base branch: `git log main..HEAD --oneline` and `git diff main...HEAD --stat`.
2. Read the most important changed files so the description is accurate, not guessed from file names.

Write this structure:

**Title**: under 70 characters, says the outcome.

**What**: 2-4 bullets of user-visible or behavior changes.

**Why**: the problem, issue link if one exists.

**How to test**: numbered steps a reviewer can follow, with the exact commands.

**Risks**: migrations, config changes, breaking API changes, performance. Write "None known" if there are none.

Keep it short. Reviewers skim; do not repeat the diff.
