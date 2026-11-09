# Change the tone

Rewrites a message in a new tone (firmer, warmer, more formal, more casual) without changing its requests or facts, in two lengths.

Replace the {{PLACEHOLDERS}} before sending.

---

Rewrite the message below so it sounds {{TONE: e.g. firmer but polite / warmer / more formal / more casual}}.

It is for: {{RECIPIENT: e.g. a client who pays late, my manager}}.
What it must achieve: {{GOAL: e.g. get paid by Friday without damaging the relationship}} (optional).

Rules:
- Keep every request, fact, date and amount. Change only wording, order and length.
- Do not add apologies, threats, promises or new information that are not in the original.
- No stock phrases ("I hope this finds you well", "per my last email", "just circling back").
- Keep the original language and the sender's point of view.

Output exactly:
**Version A** (about the original length)
**Version B** (at least 30% shorter)
**What changed:** 1-2 lines on the main wording choices, and any phrase in the original that could still read as the wrong tone.

Message:
"""
{{MESSAGE}}
"""

---

More free prompts: https://kuan-ai.com/skills/tone-shifter?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
