# Regex builder

Builds a regex from match and no-match examples, explains every part and checks each example in a test table before answering.

Replace the {{PLACEHOLDERS}} before sending.

---

Write a regular expression for {{ENGINE: e.g. JavaScript, Python re, PCRE, Go}} that matches: {{DESCRIPTION}}.
Use: {{MODE: validate the whole string / find matches inside text}}.

Must match (one per line):
{{MATCH_EXAMPLES}}

Must NOT match (one per line):
{{NON_MATCH_EXAMPLES}}

Rules:
- Use only syntax supported by that engine. State any flags needed (i, m, s, g, u).
- Prefer readable over clever. Avoid nested quantifiers that risk catastrophic backtracking.
- Trace every example through the regex before answering. If one fails, fix the regex, don't change the table.

Output exactly:
1. The regex in a code block, plus a ready-to-use line of code in that language.
2. A breakdown: each part and what it does.
3. A test table: | Example | Expected | Actual |
4. Edge cases it will get wrong. If regex is the wrong tool (nested structures, HTML, full email/URL validation), say so and name the better alternative.

---

More free prompts: https://kuan-ai.com/skills/regex-builder?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
