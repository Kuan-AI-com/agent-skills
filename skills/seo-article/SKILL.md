---
name: seo-article
description: Plan and write a blog article meant to rank in Google for a keyword. Use when the user gives a keyword or topic and asks for a blog post, SEO article, "content that ranks", or to rewrite an existing post for search.
---

# SEO article writer

## 1. Intent and competition
- Classify the intent: learn (guide), compare (X vs Y, best X), buy (product/category page, not an article), fix (troubleshooting steps). If the intent is "buy", say an article is the wrong format.
- If you have web search: look at the top results for the exact keyword. Note their format, length range, the subtopics they all cover (the baseline) and what none of them covers (your angle). If you do not have web search, say the outline is based on your judgment, not on the current results.

## 2. Collect what makes it worth ranking
Ask the user for, or mark as `[TO ADD]`:
- first-hand experience: their own tests, cases, screenshots, numbers, opinions
- product or business details the article should mention
- the site's existing pages to link to (real URLs)
An article with nothing original is a rewrite of the top 10. Say so if the user has nothing to add.

## 3. Outline (show it before writing a long article)
- H1 containing the keyword, written for a human.
- H2s that follow the order a reader needs; each answers one sub-question.
- FAQ with 3-5 questions only if you found them (People Also Ask, forums, the user's support inbox). Otherwise skip the FAQ rather than invent questions.

## 4. Write
- The first 2-3 sentences answer the query directly. No intro about the topic's importance.
- Short paragraphs, specific examples, a table or checklist where readers compare or follow steps.
- Use the keyword and close variants where natural: H1, first paragraph, one H2, meta. No stuffing.
- Length is what the topic needs, roughly in the range of what ranks. Do not pad to a word count.
- Banned filler: "In today's fast-paced world", "It's important to note", "In conclusion", "game-changer".

## 5. Facts
- Every statistic, price, date or study needs a source you opened, linked inline. If you cannot verify one, write `[SOURCE NEEDED: claim]` or remove the claim.
- Never invent quotes, studies, expert names or "according to" attributions.
- Time-sensitive facts (prices, versions, laws): add "as of <month year>".

## Output
1. Intent and angle (2 lines).
2. Meta title (<= 60 characters) and meta description (<= 155), keyword included naturally. Suggested URL slug.
3. The article in Markdown.
4. Internal links: only to URLs the user gave you, with anchor text. If none were given, say which kinds of pages to link to.
5. Checklist of every `[TO ADD]` and `[SOURCE NEEDED]` left in the text.
