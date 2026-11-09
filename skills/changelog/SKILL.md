---
name: changelog
description: Write release notes or a CHANGELOG entry from git history. Use when the user prepares a release or asks what changed since a version.
---

# Changelog from commits

1. Find the range: last tag to HEAD (`git describe --tags --abbrev=0`), or the range the user gives.
2. Read `git log <range> --no-merges` and, for unclear commits, the diff.
3. Group by impact for the user, not by commit type:
   - **Breaking changes** (first, with migration steps)
   - **New**
   - **Improved**
   - **Fixed**
4. Rewrite each item in user language: "Exports now include the customer email" instead of "feat(export): add email col".
5. Drop internal noise (refactors, CI, typo fixes) unless it affects users.
6. Follow Keep a Changelog format if the repo already has a CHANGELOG.md.
