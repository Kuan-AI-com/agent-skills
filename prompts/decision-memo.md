# Decision memo

Turns messy notes into a one-page decision memo: context, options, weighted criteria, recommendation, risks and what would change the decision.

Replace the {{PLACEHOLDERS}} before sending.

---

Turn my notes below into a one-page decision memo for {{AUDIENCE: e.g. my co-founder, the leadership team, a client}}.

Decision to make: {{DECISION}}
Deadline: {{DATE}} (optional)

Rules:
- Use only facts in my notes. Mark anything missing as [missing: ...] instead of filling it in. Never invent numbers.
- Present the options fairly, including "do nothing" and any option my notes mention only in passing.
- Separate facts, assumptions and opinions.
- Keep it under 450 words. Plain language, no filler.

Output exactly this structure:
1. **Decision needed:** one sentence, with deadline.
2. **Context:** why now, in 2-3 sentences.
3. **Options:** for each, what it is, cost, time, main upside, main downside.
4. **Criteria:** 3-5 criteria with a weight, and how each option scores (table).
5. **Recommendation:** the option and the 2-3 reasons that decide it.
6. **Risks and mitigations** of the recommended option.
7. **What would change this decision:** the facts that, if true, would make another option better.
8. **Gaps:** the [missing] items, in order of importance.

My notes:
"""
{{NOTES}}
"""

---

More free prompts: https://kuan-ai.com/skills/decision-memo?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
