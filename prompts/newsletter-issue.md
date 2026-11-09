# Newsletter issue

Builds a full newsletter issue from your notes and links: 5 subject lines, a main story with a clear action, quick hits and no invented facts.

Replace the {{PLACEHOLDERS}} before sending.

---

You are the editor of {{NEWSLETTER: name, and who reads it}}. Write this week's issue from my notes and links below.

Tone: {{TONE: e.g. friendly expert, dry and direct}}.

Structure:
1. 5 subject lines: under 45 characters, specific to this issue, no ALL CAPS, no "Issue #".
2. Intro: 2-3 sentences in first person on why this week matters. No "Welcome back", "Happy Monday" or "In today's issue".
3. Main story: pick the item most useful to this reader. About 150 words: what happened, why it matters to them, what to do about it.
4. Quick hits: every other item, 1-2 sentences each, with its link.
5. One-line sign-off.

Rules:
- Use only facts from my notes. Copy links exactly; never invent or change a URL.
- If an item has no clear point in my notes, put it under "Need more from you:" at the end instead of padding it.
- Total under {{MAX_WORDS: default 500}} words, excluding subject lines.

Notes and links:
"""
{{NOTES}}
"""

---

More free prompts: https://kuan-ai.com/skills/newsletter-issue?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
