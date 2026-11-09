---
name: changelog
description: Write release notes or a CHANGELOG.md entry from git history. Use when the user says "write the changelog", "release notes for v2.3", "what changed since the last release/tag", or is preparing a release or version bump.
---

# Changelog from commits

## 1. Fix the range
- User gave a range or versions: use it.
- Otherwise: `git describe --tags --abbrev=0` to get the last tag, range `<tag>..HEAD`.
- No tags at all: ask, or use the last CHANGELOG.md entry's date (`git log --since=<date>`). State the range you used at the top of your answer.

## 2. Collect, from the right source
- `git log <range> --no-merges --format='%h %s%n%b'` for the commits.
- If the repo squash-merges or merges PRs, PR titles carry the meaning: also read `git log <range> --merges --first-parent --format='%h %s'`.
- For any commit whose subject is vague ("fix", "wip", "updates") read `git show --stat <hash>` and the diff before classifying it. Do not guess from the message.

## 3. Detect breaking changes (check all, they are the most expensive to miss)
- `BREAKING CHANGE:` footer or `type!:` in Conventional Commits.
- Removed or renamed: public functions/exports, CLI flags, env vars, config keys, API endpoints or fields.
- Database migrations that drop/rename columns; changed defaults; raised minimum runtime versions.
Each breaking item needs a migration line: what the user must change, before -> after.

## 4. Classify by impact on the reader, not by commit type
Order: **Breaking changes**, **New**, **Improved**, **Fixed**, **Security** (if any), **Deprecated**.
Drop: refactors, CI, tests, formatting, dependency bumps with no user effect, reverted pairs (a commit and its revert cancel out). Keep a dependency bump only if it fixes a vulnerability or changes behaviour.

## 5. Rewrite each item
- User language, present tense, one line: "Exports now include the customer email" not "feat(export): add email col".
- End with the reference: `(#123)` or `(abc1234)`. Merge several commits for one feature into one line with all refs.
- Never claim an effect you did not see in the diff (performance gains, "fixes crashes"). If unsure what it changes for users, put it under **Needs review** at the end instead of guessing.

## 6. Format and placement
- If CHANGELOG.md exists, copy its exact heading and section style (often Keep a Changelog: `## [1.4.0] - 2026-11-09`). Otherwise use the order above with `##` version heading and `###` sections.
- Suggest the next version with semver: breaking -> major (minor if still 0.x), New -> minor, only fixes -> patch. Say it is a suggestion.
- Show the entry first. Write it to the file only if asked; never commit, tag or push without being asked.

## Output
1. Range used and number of commits read.
2. The entry.
3. **Needs review**: commits you could not classify, with hashes.
