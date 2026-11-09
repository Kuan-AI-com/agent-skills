---
name: pr-description
description: Write a pull request title and description for the current branch, and open the PR if asked. Use when the user says "open a PR", "create a pull request", "write the PR description", "describe my changes for review".
---

# Pull request description

## 1. Gather facts

- Base branch: the one the user names, else `git symbolic-ref refs/remotes/origin/HEAD`, else ask. Do not assume `main`.
- `git status`: if there are uncommitted changes, ask whether they belong in the PR.
- `git log <base>..HEAD --oneline` and `git diff <base>...HEAD --stat`.
- Read the diff of the files that carry the logic (skip lockfiles, generated code, snapshots). Describe what the code does, not what file names suggest.
- Linked issue: look in branch name and commit messages (`#123`, `PROJ-123`).
- Template: use `.github/pull_request_template.md` (or `PULL_REQUEST_TEMPLATE/`, `docs/`) if it exists. Fill its sections; do not replace it with your own.

## 2. Write it

**Title**: under 70 characters, the outcome. Match the repo's title convention (check recent PRs with `gh pr list --state merged --limit 10` if available).

Body (when there is no template):

```
## What
- 2-5 bullets of behavior changes, most important first.

## Why
The problem or goal in 1-3 sentences. Closes #123.

## How to test
1. Exact commands or clicks a reviewer can repeat.
2. Expected result for each.

## Risks
Migrations, config or env changes, breaking API changes, performance, rollout order. "None known" if none.

## Notes for reviewers
Where to start reading, what is mechanical (renames, moves), anything you want a second opinion on.
```

Rules:
- "How to test" lists what you or the user actually ran. If nothing was run, say so instead of inventing steps that look verified.
- Call out anything a deploy needs: new env vars, migrations, feature flags, order of deploys.
- UI change: say screenshots are needed, or attach them if available.
- Over ~400 changed lines (excluding generated files): suggest splitting, or explain the order to read it in.
- Do not paste the diff or list every file.

## 3. Open the PR (only if asked)

- Push the branch if it is not on the remote: `git push -u origin HEAD`.
- With GitHub CLI, write the body to a temp file and run `gh pr create --base <base> --title "<title>" --body-file <file>`. Add `--draft` if work is unfinished.
- Without `gh`, give the user the title and body to paste.
- Print the PR URL at the end.
