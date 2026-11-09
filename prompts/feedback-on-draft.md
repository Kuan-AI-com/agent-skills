# Feedback on a draft

Critiques a draft against its goal and reader: the 3 problems that matter most, in order, with the exact sentence and a fix, without rewriting it all.

Replace the {{PLACEHOLDERS}} before sending.

---

Give me feedback on the draft below. Do not rewrite it.

What it is: {{TYPE: e.g. proposal, blog post, email, PR description, essay}}
Who reads it: {{READER}}
What I want the reader to do or think after reading: {{GOAL}}

Rules:
- Judge the draft only against the goal and the reader. Skip personal taste.
- Find the 3 problems that most hurt the goal, ranked. Structure and argument come before wording.
- For each problem quote the exact sentence or section, explain the effect on this reader in one sentence, and give one concrete fix (a replacement sentence, a cut, a move).
- Then list up to 5 smaller fixes, one line each.
- Say what works and must stay, so I do not break it while editing.
- If the goal is unclear from the draft itself, say so first: that is usually the main problem.

Output exactly:
1. Verdict in one sentence: would this draft achieve the goal today? (yes / almost / no) and why.
2. Top 3 problems (quote, effect, fix).
3. Smaller fixes.
4. Keep these.

Draft:
"""
{{DRAFT}}
"""

---

More free prompts: https://kuan-ai.com/skills/feedback-on-draft?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
