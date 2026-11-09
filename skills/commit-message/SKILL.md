---
name: commit-message
description: Write a git commit message for the current changes and optionally make the commit. Use when the user says "commit this", "write a commit message", "commit my changes", or asks to split work into commits.
---

# Commit messages

## 1. See what will be committed

- `git status` and `git diff --staged`. If nothing is staged, show `git diff --stat` and ask what to include, or stage only the files that belong to one logical change by name. Never `git add -A` / `git add .` blindly.
- Before staging, scan for things that must not be committed: `.env*`, keys, tokens, credentials, large binaries, build output, debug prints you added. Stop and tell the user if you see one.

## 2. Learn the repo's convention

- `git log --oneline -15` for style: Conventional Commits (`feat(api): ...`), ticket prefixes (`PROJ-123`), language, capitalization.
- Check for enforced rules: `commitlint.config.*`, `.commitlintrc*`, a `commit-msg` hook in `.husky/` or `.git/hooks/`, a `CONTRIBUTING` file. Enforced rules win over this skill.

## 3. Write the message

Subject line:
- Imperative mood, at most 72 characters (50 if the repo keeps them short), no trailing period.
- Says the effect, not the file: "Retry failed webhook deliveries with backoff", not "Update webhook.ts".

Body, only when the subject is not enough:
- Blank line after the subject, wrap at 72.
- Why the change was needed and any non-obvious decision or trade-off. The diff already shows what changed.
- Footers: `Closes #123`, `BREAKING CHANGE: <what callers must change>`, co-author lines the user or repo requires.

Never claim something you did not check ("add tests", "fix crash") unless the diff shows it.

## 4. Split when needed

If the staged diff mixes unrelated changes (a refactor plus a bug fix, formatting plus logic), propose separate commits with a message for each and the file list. Stage them separately with `git add <paths>` or `git add -p` when the user agrees.

## 5. Commit (only if the user asked to commit)

Pass multi-line messages through a heredoc so newlines survive:
```
git commit -F - <<'EOF'
Subject line

Body text.
EOF
```
- If a hook fails, read the output, fix the cause (lint, format, tests) and commit again. Do not use `--no-verify` unless the user explicitly says so.
- Do not `--amend` a commit that is already pushed, and do not push unless asked.
- After committing, show `git log -1 --stat` so the user sees the result.
