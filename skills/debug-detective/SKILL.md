---
name: debug-detective
description: Find the root cause of a bug, crash, error message or failing test, then fix it. Use when the user says "this is broken", "why does this fail", "I get this error", "the test is failing", "it worked yesterday", or pastes a stack trace.
---

# Systematic debugging

Work from evidence. Every edit you make should either gather information or fix a cause you can explain.

## 1. Reproduce

- Get the exact command, input, environment and the full error output (not a summary). Run it yourself if you can.
- Make the reproduction as small and fast as possible: a single test, a script, one request with curl.
- Cannot reproduce? List the differences between your run and theirs (env vars, versions, data, OS, config, cache, timezone) and ask for the missing ones. Do not guess-fix a bug you have not seen.

## 2. Read the error literally

- Read the whole message and the first frame in the project's own code. Look at the line, and the values that reach it.
- For "works on my machine", compare versions: lockfile, runtime (`node -v`, `python --version`), env vars, data.

## 3. Ask what changed

If it used to work: `git log --oneline -20 -- <relevant paths>`, recent dependency updates, config or data changes. If there is a known good commit and a quick check, use `git bisect` (`git bisect run <command>` when the check is scriptable).

## 4. Hypothesize and test

- Write 2-3 hypotheses ranked by likelihood. For each, name the observation that would confirm or rule it out.
- Test the cheapest one first: print a value, add an assertion, run with a debugger, call the function with the failing input.
- Change one thing at a time. Revert any change that did not help before trying the next.

Stop rule: if three hypotheses fail, step back. Re-check your assumptions (is the code you are reading the code that runs? stale build, wrong branch, cached module, different config file), and share what you have ruled out with the user.

## 5. Fix the cause

- State the cause in one sentence: "X fails because Y, introduced in Z".
- Fix it where it originates, not where it surfaces.
- Add a test that fails before the fix and passes after. Run the related test suite.
- Search for the same pattern elsewhere (`git grep`) and list other places with the same bug.

## Do not

- Silence the symptom: empty catch blocks, `|| true`, skipping or deleting the test, longer timeouts, retries around a deterministic failure.
- Stack several speculative fixes and keep whichever "works".
- Leave debug prints, breakpoints or temporary flags behind. Remove them before reporting.

## Report

- Root cause (one sentence) and the evidence that proves it.
- The fix (files changed) and the test that covers it.
- Other places affected, and anything you could not verify.
