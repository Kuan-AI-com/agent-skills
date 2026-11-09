---
name: support-reply
description: Draft a reply to a customer support message, ticket, review or chat. Use when the user pastes a customer message and asks how to respond, "answer this ticket", "reply to this complaint", or wants a support macro or template.
---

# Customer support reply

## 1. Triage
- What does the customer want (refund, fix, information, to be heard)? List every issue if there are several.
- Type: bug, how-to question, billing, shipping/delivery, account access, feature request, complaint.
- Mood: calm, frustrated, angry, threatening to leave.

## 2. Escalate instead of answering alone when the message involves
legal threats or lawyers, chargebacks or fraud, safety or injury, a security vulnerability or account compromise, data deletion/access requests (GDPR, CCPA), press or public social media posts, or a refund/credit above what the policy lets you grant.
Then draft a short holding reply (received, who will follow up, when if known) and an internal note saying why it needs a human.

## 3. Check the source of truth
Read the policy, FAQ, docs or macros available in the project or conversation (refunds, shipping, SLAs, warranty). If none are available, write the reply with `[policy: ...]` placeholders. Never:
- promise anything the policy does not allow
- invent timelines ("within 24 hours") without a stated SLA
- state account facts you cannot see (order status, tracking, plan) -> use `[order status]`
- say an action is done ("I've issued a refund") unless the user told you it is done. Write "I've requested..." or `[confirm refund issued]`.

## 4. Draft
- First sentence names their specific problem, not "we apologize for any inconvenience". Apologise once if we are at fault; do not admit fault for things not yet confirmed.
- The answer or fix. Steps as a numbered list, one action per step, using the exact names of buttons and menus from the docs.
- What happens next and who acts: "You'll get an email from us when...".
- If information is missing (order number, email, screenshot, device), ask for all of it in one list.
- Under 120 words unless steps require more. Customer's language. No internal jargon or ticket codes. Never blame the customer.
- Sign with `[Agent name]`.

## 5. Internal note (separate, only if useful)
Bug to report (steps, frequency), doc gap, policy exception requested, or churn risk.

## Output
1. Triage line: type, mood, escalate yes/no.
2. The reply.
3. Placeholders to fill.
4. Internal note, if any.
