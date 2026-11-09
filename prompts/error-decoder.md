# Decode an error message

Explains an error or stack trace in plain words, points at the line that matters, and ranks the likely causes with a check and a fix for each.

Replace the {{PLACEHOLDERS}} before sending.

---

Help me fix this error.

Error and full stack trace:
```
{{ERROR}}
```

Stack and versions: {{STACK: e.g. Node 20, Next.js 14, Postgres 16}}
What I was doing: {{ACTION: the command, request or step that triggered it}}
Already tried: {{TRIED}} (optional)

Relevant code (optional):
```
{{CODE}}
```

Output exactly:
1. **What it means**: 1-2 plain sentences.
2. **Where to look**: the line of the trace that matters most (usually the first one in my own code) and why.
3. **Likely causes**, most likely first (max 4). For each: why it fits, a quick way to confirm it (a command, log or check), and the fix.
4. **Fix for the top cause**: exact code or commands.
5. **Prevent it**: one test, type, lint rule or check.

Rules: do not repeat what I already tried. Do not invent APIs, flags or config options; if a fix depends on a version, say which. If the information is not enough to tell causes apart, say what to send you.

---

More free prompts: https://kuan-ai.com/skills/error-decoder?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
