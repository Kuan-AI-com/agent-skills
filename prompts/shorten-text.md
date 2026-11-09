# Shorten a text

Cuts a text to a word target while keeping the point, the key facts and the author's voice, then reports exactly what was removed.

Replace the {{PLACEHOLDERS}} before sending.

---

Shorten the text below to at most {{MAX_WORDS: e.g. 150; default: half the original}} words.

Keep, in this order of priority:
1. The main point and the call to action.
2. Numbers, names, dates, deadlines and conditions.
3. The author's voice, person ("I", "we") and language.

Cut first: repetition, warm-up intros, hedges ("I think", "basically", "just"), filler adjectives, and examples that repeat a point already made.

Do not summarize in the third person: it must still read as the original text, ready to send. Do not add new words or ideas.

Count the words before answering. If you are over the limit, cut again.

Output exactly:
1. The shortened text (no preamble).
2. "Word count: X (was Y)".
3. "Cut:" one line listing what you removed. Flag anything important you had to drop to hit the limit.

Text:
"""
{{TEXT}}
"""

---

More free prompts: https://kuan-ai.com/skills/shorten-text?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
