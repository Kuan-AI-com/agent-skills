# Explain this code

Understand unfamiliar code fast: purpose, step-by-step flow, side effects, hidden assumptions and likely bugs, without rewriting it.

Replace the {{PLACEHOLDERS}} before sending.

---

Explain the code below to a developer who knows {{LANGUAGE}} but has never seen this codebase.
Why I'm reading it: {{GOAL: e.g. fix a bug in it, review it, extend it}} (optional)

1. **Purpose**: what it does, in 2 sentences.
2. **Flow**: step by step, referencing function names or line numbers.
3. **Inputs, outputs, side effects**: I/O, network, database, global or shared state, mutation of arguments.
4. **Non-obvious parts**: tricks, implicit assumptions, ordering or timing dependencies.
5. **Risks**: possible bugs and unhandled edge cases, each tagged [likely] or [possible], with the input that would trigger it.

Rules:
- If behavior depends on code that is not shown (imports, called functions), say what you are assuming instead of guessing.
- Do not rewrite or refactor the code. Short snippets only to point at a line.
- Focus the depth on what matters for my goal. Under 500 words.

```
{{CODE}}
```

---

More free prompts: https://kuan-ai.com/skills/explain-code?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
