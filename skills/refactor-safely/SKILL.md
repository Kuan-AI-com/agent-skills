---
name: refactor-safely
description: Refactor code without changing what it does (rename, extract, split files, remove duplication, simplify). Use when the user says "clean this up", "refactor", "split this file", "simplify this function", "rename X everywhere", or "remove this duplication".
---

# Safe refactoring

A refactor changes structure, not behavior. Behavior includes return values, thrown errors and their messages, side effects and their order, public names and types, and log or event output that other systems read.

## 1. Scope it

State in one or two sentences what will change and what will not. If the user's request implies a behavior change ("and make it faster", "and fix the edge case"), split that into a separate step after the refactor.

## 2. Baseline

- Find and run the checks the project has: tests, type checker (`tsc --noEmit`, `mypy`, `go vet`), linter. Get the commands from `package.json`, `Makefile`, CI config.
- Record what passes now. Pre-existing failures are not yours to fix; note them.
- If the code you will touch has no tests, write characterization tests that pin its current output for typical and edge inputs, including current odd behavior. Do not refactor untested code you cannot run.

## 3. Find every usage

Before renaming or moving anything, search for it in all forms:
- static references (`git grep -n`, editor "find references")
- dynamic ones: string keys, `getattr`/reflection, dependency-injection names, route names, template and config files, serialized data, SQL column names
- external consumers: exported package API, HTTP or event contracts, other repos. If it is public, keep the old name as a deprecated alias or ask first.

## 4. Change in small steps

- One mechanical move per step: rename, extract function, inline, move file, replace conditional with lookup.
- After each step, run the fast checks (affected tests and the type checker). If something breaks, fix or revert that step before continuing.
- Prefer tooling for renames and moves (IDE refactor, `git mv`) over hand edits so history and references follow.
- If the user is using git, suggest a commit per meaningful step so each one can be reverted alone.

## 5. Stay in scope

- Do not fix bugs you find mid-refactor; list them and fix later as separate changes (a bug fix changes behavior and the tests should show it).
- Do not reformat unrelated code or change style across files you only passed through.
- If the refactor grows past what was agreed (more files, a new abstraction), stop and check with the user.

## 6. Verify and report

- Run the full baseline again; results must match.
- Read your own final diff once, looking for accidental logic changes: flipped conditions, changed defaults, reordered side effects, dropped `await`, changed error types.
- Report: what moved where, why the new shape is simpler, the checks you ran with results, and any bugs or follow-ups you noticed but did not touch.
