---
name: write-tests
description: Write unit or integration tests for a function, module or bug fix. Use when the user asks for tests or test coverage.
---

# Write tests

1. Find the test setup: look for jest/vitest/pytest/go test config and an existing test file next to similar code. Copy its style, helpers and naming.
2. List the behaviors to cover before writing code:
   - the main happy path
   - edge cases: empty input, boundaries, unicode, large values
   - error paths: invalid input, failing dependency
   - the bug being fixed, as a test that fails without the fix
3. One behavior per test. Name tests as sentences: "returns 0 for an empty cart".
4. Mock only what you do not own (network, clock, randomness). Do not mock the code under test.
5. Run the tests. Show the command and the result. If a test fails, decide whether the test or the code is wrong and say which.
