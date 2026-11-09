---
name: eval-prompt
description: Design and run a small evaluation for a prompt, system prompt, Agent Skill or LLM feature, and compare versions. Use when the user asks "is this prompt better?", "test my skill", "evaluate the agent", "build an eval", or wants to change a prompt without breaking what works.
---

# Evaluate a prompt or skill

Opinions about a prompt are worthless until it runs on the same cases before and after. Keep the eval small enough to run often.

## 1. Define success

- What the prompt or skill must do, for whom, and what output a real user would accept.
- Write 3-6 criteria, each checkable as pass/fail: "cites only facts from the input", "returns valid JSON with fields a, b, c", "under 150 words", "asks for missing order number instead of inventing one". Avoid vague criteria like "good quality".
- Mark which criteria are hard failures (wrong facts, unsafe output, broken format).

## 2. Build the test set

10-30 cases, saved in a file (`evals/cases.jsonl` or similar) so the eval is repeatable:
- **typical:** the common real inputs (use real examples, anonymised, if the user has them)
- **edge:** empty, very long, other language, messy formatting, several requests in one
- **adversarial:** missing information, conflicting instructions, a tempting wrong answer, injection text inside the input
- **regression:** every bug a user has reported

For each case write the expected behaviour, not necessarily the exact text.

## 3. Grade

- Use code checks wherever possible: JSON schema, regex, length, required fields, exact answers.
- For judgement criteria, use a grader prompt with the rubric and one criterion per question, answering pass/fail with a one-line reason. Spot-check at least a few graded outputs by hand; if the grader disagrees with you, fix the grader first.
- Run each case more than once (3 runs if cost allows) when the model is not deterministic. Report pass rate, not a single lucky run.

## 4. Compare versions

- Baseline first: run the current version and save the results.
- Change one thing at a time. Run the same cases with the same model and settings.
- Look at the cases that flipped (pass to fail and fail to pass), not only the total. A higher score that breaks a hard-failure case is a regression.
- With fewer than ~30 cases, a difference of one or two cases is noise. Say so.

## Do not

- Tune the prompt on the exact cases you report as the result without saying so. Keep a few cases aside if the user will rely on the number.
- Invent model outputs or scores. If you cannot call the model, deliver the cases, the rubric and the script, and say the eval has not run.

## Output

1. Criteria (with hard failures marked).
2. Test cases file.
3. Grading method (code checks + grader prompt).
4. Results table: version, pass rate per criterion, flipped cases.
5. Recommendation and the cases that still fail.
