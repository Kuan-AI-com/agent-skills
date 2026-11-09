---
name: meeting-notes
description: Turn a meeting transcript, recording summary or rough notes into structured notes. Use when the user pastes a transcript, says "summarize this meeting", "write the minutes", "recap", "what are the action items", or wants a follow-up email after a call.
---

# Meeting notes

## Before writing
- Find the meeting date (transcript header, file name, or ask). You need it to turn "next Friday" into a date. Without it, keep the relative phrase in quotes.
- Identify speakers. If the transcript uses "Speaker 1/2" or labels are unreliable, keep those labels; never guess who said something.
- Transcripts from speech recognition mangle names, product names and numbers. When something looks misheard, keep it and mark it `[?]`.

## Output (exactly these sections, in this order)

**Summary**: up to 3 sentences: purpose of the meeting and what came out of it.

**Decisions**: only what was clearly agreed ("let's go with X", "agreed", no objection after a proposal by the person who owns it). A suggestion nobody confirmed is not a decision: put it in Open questions as "Proposed: ...".

**Action items**

| Task | Owner | Due | Source |
|---|---|---|---|
| Send revised quote to ACME | Maria | 2026-11-14 (said "Friday") | ~12:40 |

- Task starts with a verb and is specific enough to do without the transcript.
- Owner: the person who committed ("I'll do it") or was explicitly assigned. Otherwise `unassigned`.
- Due: only if said. Otherwise `no date`. Never invent one.
- Source: timestamp or a short quote, so it can be checked.

**Open questions**: raised but not resolved, with who raised them.

**Numbers and commitments** (only if any): prices, dates, quantities, promises to customers, quoted exactly.

## Rules
- Nothing that is not in the source. No "next steps" you think would be wise; if you have a suggestion, put it after the notes under "Suggestion (not from the meeting)".
- Long meetings with several topics: group Decisions and Action items by topic heading.
- Write in the language of the transcript unless asked otherwise.
- Drop small talk, but keep anything that changes a task, a date or a risk.

## Follow-up email (only if asked)
Subject "Recap: <topic> (<date>)", 2 lines of context, then Decisions and Action items as above. No added commitments.
