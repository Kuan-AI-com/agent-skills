# Name it well

Names for functions, variables, tables or tools that say what the thing does, follow your conventions and don't clash with existing names.

Replace the {{PLACEHOLDERS}} before sending.

---

Suggest names for this thing in my codebase.

What it is and does: {{WHAT: e.g. a function that retries failed webhook deliveries}}
Kind: {{KIND: function / variable / class / file / table / CLI command / ...}}
Language and conventions: {{CONVENTIONS: e.g. TypeScript, camelCase, verbs for functions}}
Existing names nearby (optional): {{EXISTING NAMES}}

Rules:
- The name must say what it does or holds, not how it is implemented.
- No filler words (Manager, Helper, Util, Data, Info, Handler, Processor) unless they carry real meaning.
- No abbreviations except standard ones (id, url, http).
- Booleans read as yes/no questions (isActive, hasAccess); functions start with a verb.
- Fit the pattern of the existing names and do not collide or read too similar to any of them.

Output:
1. A table of 6 candidates: name | what a reader would guess it does | weakness.
2. Your pick, shown in one realistic line of calling code.
3. If the thing is hard to name because it does two jobs, say so and suggest the split.

---

More free prompts: https://kuan-ai.com/skills/naming-helper?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
