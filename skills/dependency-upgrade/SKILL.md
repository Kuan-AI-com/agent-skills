---
name: dependency-upgrade
description: Upgrade a dependency, framework or runtime to a new version, especially a major one (React, Next.js, Django, Rails, Node, Python, a library with breaking changes). Use when the user says "upgrade X", "bump to v5", "fix this deprecation", or a security advisory requires a newer version.
---

# Upgrade a dependency

## 1. Know where you are and where you go

- Current version from the lockfile (the installed one, not only the range in the manifest) and the target version. If the user said "latest", look it up and state the exact number.
- The package manager and its version (npm, pnpm, yarn, pip, poetry, uv, bundler, cargo, go).
- Why: security fix, needed feature, end of support. It decides how far to go.

## 2. Read before touching

- The changelog and the official migration guide for every major version between current and target. Do not skip intermediate majors: their breaking changes still apply.
- Peer dependencies and plugins that must move together (types packages, framework plugins, lint configs).
- The minimum runtime version the new release needs.
- Codemods the maintainers publish. Prefer them to manual edits.
- If you cannot open the changelog, say so and work from compiler errors and tests, flagging that behaviour changes may be missed.

## 3. Get a baseline

Run the test suite, type check, lint and build on the current version first. Record what already fails so you do not blame the upgrade for it.

## 4. Upgrade in steps

- One major version at a time for big jumps. One package (or one group that must move together) per commit.
- Update with the package manager so the lockfile changes properly. Do not hand-edit lockfiles.
- After each step: install, build, type check, tests. Fix what breaks before going further.
- Search the code for every removed or renamed API listed in the guide (`git grep`), not only the ones the compiler finds. Behaviour changes (defaults, ordering, timezones, error types) do not show up as compile errors.

## 5. When something breaks

- Read the error against the migration guide first.
- Do not silence it with `any`, `@ts-ignore`, `--legacy-peer-deps`, `--force` or version overrides unless there is no other way. If you must, list each one in the report.
- Stuck after reasonable effort? Stop at the last green step, commit it, and report what blocks the next one.

## Report

1. From version, to version, and the intermediate steps taken.
2. Breaking changes that affected this code and how each was handled.
3. Results of build, type check and tests (before and after).
4. Workarounds or suppressions added, and follow-ups.
5. What to check manually (behaviour changes not covered by tests).
