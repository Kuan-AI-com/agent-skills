---
name: ci-failure-fix
description: Diagnose and fix a failing CI pipeline (GitHub Actions, GitLab CI, CircleCI, Jenkins...). Use when the user says "CI is red", "the build fails", "checks are failing on my PR", "it passes locally but fails in CI", or pastes a CI log.
---

# Fix a failing CI build

## 1. Get the real log

- GitHub Actions: `gh run list --branch <branch> -L 5`, then `gh run view <id> --log-failed`. GitLab: the failed job's log. Otherwise ask for the full log of the failed step, not a screenshot.
- Find the first error, not the last line. Later failures are often consequences.
- Note which job, step, runner OS and runtime version failed.

## 2. Classify

- **Real failure from this change:** fails consistently, related to the diff.
- **Already broken on the base branch:** check the latest run on main. If main is red too, say so; the fix may not belong in this PR.
- **Flaky:** passed on re-run with the same commit, or fails at random places (timeouts, ordering, network, time zones, shared state). Check the run history before calling it flaky.
- **Environment:** CI-only differences: runtime or tool version, missing secret (forks do not get secrets), cache, OS (case-sensitive paths on Linux, line endings on Windows), timezone, locale, CPU count, missing system package.

## 3. Reproduce locally

- Use the exact command from the workflow file, not your usual one.
- Match the CI environment: same runtime version (read the workflow and `.nvmrc`, `.tool-versions`, `python-version`), clean install from the lockfile (`npm ci`, `pip install -r`, `bundle install --frozen`), the same env vars, `CI=true`.
- Still passes locally? Diff the environments one by one. For containers, run the job image locally. Ask the user for access only if you truly need it.

## 4. Fix the cause

- Code bug: fix it and add or keep the test that caught it.
- Test bug (order dependence, real clock, real network, shared fixtures): make the test deterministic.
- Environment: pin the version, add the missing setup step or fix the path. Explain why CI differed.
- Lockfile drift: regenerate it with the project's package manager and version.

## Do not

- Skip, delete or mark the test as expected-to-fail, add `continue-on-error`, lower coverage thresholds, or increase timeouts to make CI green, unless the user explicitly agrees and you record why.
- Re-run until it passes and call it fixed.
- Print or change secrets. If a secret is missing, tell the user which one and where to set it.

## Report

1. Failing job and step, and the first real error (quoted).
2. Classification and the evidence for it.
3. Cause in one sentence.
4. The fix, and proof: the command you ran locally and its result, or the new CI run.
5. Anything still unverified (for example, it needs a secret you cannot see).
