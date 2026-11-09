# Translate code to another language

Ports code to another language idiomatically, keeps behavior identical, flags what can't map 1:1 and adds tests that prove it.

Replace the {{PLACEHOLDERS}} before sending.

---

Translate this {{FROM LANGUAGE}} code to idiomatic {{TO LANGUAGE}}.
Target version / framework (optional): {{TARGET VERSION}}
Allowed dependencies (optional, default: standard library only): {{DEPENDENCIES}}

Rules:
- Idiomatic target code (its standard library, error handling and naming), not a line-by-line port.
- Same behavior, including errors, edge cases and public names/signatures where the language allows.
- Do not fix bugs or add features silently. If you spot a bug in the original, keep the behavior and list it.
- Where behavior cannot map exactly (integer overflow, null/undefined, floating point, string encoding, concurrency, mutability), choose the closest safe equivalent and say what changed.

Output:
1. The translated code, in one code block.
2. Mapping notes: a table of original construct | target construct | behavior difference (if any).
3. Tests in the target language covering the normal path, edge cases and error cases.
4. Bugs or ambiguities found in the original.

```
{{CODE}}
```

---

More free prompts: https://kuan-ai.com/skills/translate-code?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
