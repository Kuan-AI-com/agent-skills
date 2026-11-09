---
name: commit-message
description: Write a git commit message for the staged changes. Use when the user asks to commit, or asks for a commit message.
---

# Commit messages

1. Run `git diff --staged`. If nothing is staged, run `git status` and ask what to include. Never stage secrets (.env, keys, credentials).
2. Run `git log --oneline -10` and match the repo's style (Conventional Commits, prefixes, language).
3. Write:
   - Subject: imperative mood, at most 72 characters, no trailing period. Say what changes for the user or the code, e.g. "Retry failed webhook deliveries" rather than "Update webhook.ts".
   - Body (only if the why is not obvious): wrap at 72, explain the reason and any trade-off. Mention breaking changes explicitly.
4. One logical change per commit. If the diff mixes unrelated changes, propose splitting it.
