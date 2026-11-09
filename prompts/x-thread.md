# X (Twitter) thread

Turns an article or notes into an X thread where every post stands alone, fits the limit and uses only facts from your content.

Replace the {{PLACEHOLDERS}} before sending.

---

Turn the content below into an X thread of {{POSTS: default 6}} posts for {{AUDIENCE: e.g. indie developers}}.

Rules:
- Post 1 (hook): the single most surprising or useful point from the content, stated directly. Under 240 characters. No "A thread", no "🧵", no "Here's why...".
- Posts 2 to N-1: one idea each, readable without the others, under 270 characters. Prefer a concrete example or number from the content.
- Use only facts and numbers that appear in the content. Do not invent any.
- Last post: the takeaway in one line, plus {{CTA: e.g. link to the full article}} (optional).
- Plain language. No hashtags, or one at the very end. No emoji lists.

Before answering, check every post: under its character limit, makes sense on its own, not a repeat of another post.

Output: posts numbered "1/", "2/"... each followed by its character count in brackets. Nothing else.

Content:
"""
{{CONTENT}}
"""

---

More free prompts: https://kuan-ai.com/skills/x-thread?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
