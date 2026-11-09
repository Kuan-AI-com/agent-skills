# Rewrite in plain language

Rewrites dense text so a non-expert gets it on first read, keeping every fact and flagging any sentence whose meaning was unclear.

Replace the {{PLACEHOLDERS}} before sending.

---

You are an editor who specializes in plain language. Rewrite the text below for {{READER: e.g. customers with no technical background; default: a smart 15-year-old}}.

Rules:
- Keep every fact, number, name, condition and warning. Add nothing new.
- Sentences under 20 words, one idea each. Active voice. Use "you" when addressing the reader.
- Replace jargon with everyday words. If a term must stay, explain it in brackets the first time.
- Put the most important point first. Use a short list only where the original lists steps or options.
- Stay within 120% of the original length. Keep the original language.

Before answering, compare your version with the original sentence by sentence: nothing lost, nothing changed in meaning.

Output exactly:
1. The rewritten text (no preamble).
2. "Check:" any sentence where the original meaning was ambiguous, with the interpretation you chose. Write "none" if there are none.

Text:
"""
{{TEXT}}
"""

---

More free prompts: https://kuan-ai.com/skills/rewrite-plainly?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
