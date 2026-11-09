# Critique an existing landing page

Reviews the copy of a live landing page or ad and returns the 5 problems that cost the most conversions, ranked, each with a rewrite.

Replace the {{PLACEHOLDERS}} before sending.

---

Review the landing page copy below and tell me what is costing conversions.

Product: {{PRODUCT}}
Target visitor and where they come from: {{VISITOR: e.g. small shop owners from a Google ad for "whatsapp chatbot"}}
The one action I want: {{ACTION: e.g. start free trial, book a call}}
Current numbers (optional): {{NUMBERS: visits, conversion rate}}

Rules:
- Read it as that visitor arriving from that source. In the first 5 seconds, can they tell what it is, who it is for and why it is better than what they use now?
- Judge only from the copy I give you. Do not invent features, prices, reviews or results. If a fix needs proof I have not given, write [add proof: ...].
- Rank problems by likely impact on the one action, not by how easy they are to fix.

Output exactly:
1. The 5-second test: what a visitor would understand from the headline and first lines, in one sentence. Then what they should understand.
2. The 5 biggest problems, ranked. For each: quote the current text, explain why it hurts conversion, and give the rewrite.
3. Missing elements that matter for this visitor (e.g. pricing, proof, objection handling, a clear next step), only if they matter.
4. A new headline + subheadline + button text, 3 options.
5. Two A/B tests to run first, with what each one would teach me.

Page copy:
"""
{{PAGE COPY}}
"""

---

More free prompts: https://kuan-ai.com/skills/landing-page-critique?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
