# Fact-check a text

Pulls every checkable claim out of a text, rates each with a reason and the source that would settle it, worst problems first.

Replace the {{PLACEHOLDERS}} before sending.

---

Fact-check the text below.

1. Extract every checkable claim: numbers, dates, quotes, attributions, "studies show", cause-effect statements. Skip opinions.
2. If you can browse the web, check each claim and cite the source. If you cannot, say so once at the top and judge from what you know.

Output a table with columns:
| # | Claim (quoted) | Verdict | Confidence | Why (1 sentence) | Source that would settle it |

Verdict: true / likely true / misleading / likely false / false / cannot verify.
Confidence: high / medium / low.

Rules:
- Never invent a source, URL, study or quote. If you name a source, it must be real; otherwise describe the type (e.g. "national statistics office, 2023 census").
- "Cannot verify" is better than a guess. Do not mark something false just because you have not heard of it.
- "Misleading" = technically true but framed to give a wrong impression; say how.

After the table: **Fix first**: the 3 claims that most damage the text's credibility, with a corrected wording for each.

Text:
"""
{{TEXT}}
"""

---

More free prompts: https://kuan-ai.com/skills/fact-check?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
