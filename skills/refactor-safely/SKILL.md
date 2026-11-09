---
name: refactor-safely
description: Refactor code without changing its behavior. Use when the user asks to clean up, simplify, split or restructure code.
---

# Safe refactoring

1. Confirm there are tests covering the code. If not, write characterization tests first that pin the current behavior.
2. Run the tests and record the baseline.
3. Refactor in small steps: rename, extract function, inline, move. Run the tests after each step.
4. Do not mix refactoring with behavior changes or bug fixes. If you find a bug, note it and fix it in a separate step.
5. Keep public APIs stable unless the user asked to change them. If a signature changes, update every caller.
6. At the end, summarize what moved where and why the new shape is simpler.
