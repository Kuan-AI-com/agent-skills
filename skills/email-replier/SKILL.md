---
name: email-replier
description: Draft a reply to an email, Slack or LinkedIn message. Use when the user pastes a message and says "reply to this", "how should I answer", "draft a response", "write back saying no/yes", or forwards a thread to answer.
---

# Email replies

## 1. Read the whole thread
- Every question and request addressed to the user, numbered. Include implicit ones ("let me know if Tuesday works" is a question).
- What was already promised or said earlier in the thread, so the reply does not contradict it.
- Who else is on the thread and whether the reply should be reply-all.

## 2. Find the decisions that only the user can make
Accept or decline, price, date, scope, whether to apologise or admit a mistake. If the user did not say:
- one decision missing: draft the most likely version and say which assumption you made at the top, or
- the decision changes the whole reply (yes vs. no): ask one short question before drafting, or give both versions.
Never commit the user to a date, discount, deliverable or admission of fault they did not state.

## 3. Draft
- First line answers the main point. No "I hope this email finds you well", no "Just following up".
- Then each remaining question in the sender's order, one short paragraph or bullet each. Every numbered item from step 1 is answered or explicitly deferred ("I'll confirm the budget by Thursday").
- End with one next step: who does what, by when.
- Match the sender's register and length. Short casual message -> short casual reply. Write in the sender's language unless told otherwise.
- Default under 150 words; go longer only when there are many questions.
- Missing facts (prices, dates, links, attachments) go in visible `[brackets]`. Never invent them.
- If the user has a known style or signature in context, use it; otherwise sign with `[Name]`.

## 4. Check before showing
- Every question answered? Count against the list.
- Any promise in the draft the user did not authorise? Remove it or turn it into a `[bracket]`.
- Tone: would this read as rude, passive-aggressive or grovelling to the recipient? Fix it.

## Output
- Subject line only if it is a new thread or the subject should change.
- The draft.
- One line under it: assumptions made and placeholders to fill.

Never send the email or message yourself, even if a mail tool is available, unless the user explicitly asks to send it.
