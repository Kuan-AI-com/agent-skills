# Summarize a paper or long report

Extracts a paper's claim, method, real numbers and weak spots, checks whether the evidence backs the headline, all from the text only.

Replace the {{PLACEHOLDERS}} before sending.

---

Summarize the paper or report below for {{AUDIENCE: e.g. a busy engineer, an investor}}. Use only the text I provide; if a section is missing, say so.

Output exactly these sections, under 400 words in total:
- **Claim**: one sentence, what they say they found.
- **Why it matters**: 2 sentences, for this audience.
- **Method**: design, data, sample size, time period.
- **Key results**: the actual numbers, each with the section or page it comes from.
- **Does the evidence support the claim?** Strong / partial / weak, with one sentence why (e.g. correlation presented as cause, small sample, no control group).
- **Limitations**: what the authors admit, then what they do not mention.
- **Takeaways**: 2-3 practical actions for this audience.

Rules: never add numbers or facts that are not in the text. If something is unclear, write "unclear in text" instead of guessing.

Paper:
"""
{{PAPER_TEXT}}
"""

---

More free prompts: https://kuan-ai.com/skills/summarize-paper?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
