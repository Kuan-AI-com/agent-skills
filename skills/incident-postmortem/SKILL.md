---
name: incident-postmortem
description: Write a blameless postmortem or incident report from logs, alerts, chat transcripts, tickets and notes. Use when the user says "write the postmortem", "incident report", "RCA", "what happened during the outage", or pastes an incident timeline or Slack thread.
---

# Incident postmortem

The goal is learning, not blame. Describe what systems and processes allowed the failure, never "X made a mistake".

## 1. Collect and separate facts

- Gather every source provided: alerts, logs, deploy history, chat, tickets, status page updates.
- Mark each statement as **confirmed** (seen in logs, metrics or a timestamped message) or **reported** (someone said so). Keep that distinction in the document.
- Use one time zone throughout (UTC unless the team uses another) and convert every timestamp to it.

## 2. Build the timeline

Key moments, each with time, event and source:
- trigger (the change or event that started it)
- start of customer impact
- detection (and how: alert, customer, employee)
- escalation and responders joining
- mitigation steps, including the ones that did not work
- impact ends
- full resolution

Never invent or round a time you do not have. Write `[time unknown]` and add it to the open questions.

## 3. Impact

- Who was affected, what they could not do, for how long.
- Measured numbers (failed requests, affected users, orders, revenue) only from data provided. Estimates must be labelled as estimates, with the method.
- Detection time (start to detection) and resolution time (start to end).

## 4. Causes

- **Root cause:** the underlying condition that, if it had not existed, would have prevented the incident. Ask "why" until you reach something a team can change (a missing check, a design gap, an unclear process), not a person.
- **Trigger:** what set it off. Often different from the root cause.
- **Contributing factors:** what made it worse or slower to fix (missing alert, confusing dashboard, runbook out of date, on-call could not access X).
- **What went well:** keep it; it shows what to protect.

If the evidence does not prove a cause, write "most likely" and what would confirm it.

## 5. Action items

Each one: specific action, owner (a role or `[owner]`), priority, due date or `[date]`, and which cause it addresses. Prefer actions that prevent or detect the whole class of failure over one-off patches. Five strong items beat fifteen vague ones.

## Output

1. Title, date, severity, status, author `[name]`.
2. Summary (3-4 sentences a non-engineer can read).
3. Impact.
4. Timeline (table).
5. Root cause, trigger, contributing factors.
6. What went well / what went badly / where we got lucky.
7. Action items (table).
8. Open questions and missing data.
