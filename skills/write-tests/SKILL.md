---
name: write-tests
description: Write unit or integration tests for a function, module, endpoint or bug fix, in the project's existing test framework. Use when the user says "add tests", "write tests for this", "increase coverage", "test this bug fix", or "why isn't this tested".
---

# Write tests

## 1. Find how this project tests

- Test command: `package.json` scripts, `Makefile`, `pyproject.toml`/`pytest.ini`/`tox.ini`, `go.mod`, `Cargo.toml`, CI config in `.github/workflows/`. Use that command, not a guessed one.
- Find the nearest existing test for similar code and copy its location, naming, imports, fixtures, factories and mocking style. Do not add a new framework or assertion library.
- Run the existing suite (or the relevant file) once before writing, so you know the baseline. If it is already red, tell the user before adding to it.

## 2. Read the code under test

Read the function and its callers. The behaviors worth testing are what callers rely on: return values, thrown errors, side effects (DB writes, events, calls to other services). Not private helpers or the order of internal calls.

## 3. Plan cases before coding

Write a short list, then implement:
- the main path with realistic input
- boundaries that matter for this code: empty, one, many, max length, zero, negative, missing optional fields, duplicates
- error paths: invalid input, dependency failure or timeout, permission denied
- for a bug fix: the exact input from the bug report

Skip cases that only re-test the language or a library.

## 4. Write them

- One behavior per test; name it as a sentence: "rejects an expired coupon".
- Arrange / act / assert, visible in the test. Prefer explicit expected values over recomputing them with the same logic as the code.
- Mock only boundaries you do not control: network, clock, randomness, third-party APIs. Use the project's real DB test setup if it has one.
- Deterministic: freeze time, seed randomness, no reliance on test order or shared mutable state, no real sleeps.
- Avoid large snapshots; they get approved without being read.

## 5. Prove each test can fail

A test that cannot fail is worse than none. For each new test, break the behavior (flip a condition, return early, comment out the fix) and confirm the test goes red, then restore. For bug-fix tests, confirm it fails without the fix.

## 6. Run and report

- Run the new test file first, then the whole affected suite. Show the command and the pass/fail counts.
- If a test fails because the code is wrong, do not change the assertion to match. Report: "this looks like a bug: <input> gives <actual>, expected <expected>", and ask before fixing production code.
- Do not modify production code just to make it testable without saying so and why.

Summary at the end: which behaviors are now covered, which you deliberately left out, and any bugs found.
