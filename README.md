# KuanAI free agent skills

20 ready-to-use **Agent Skills** (`SKILL.md`) for Claude Code, Claude.ai and any agent that reads the Agent Skills format, plus 30 copy-paste prompts. Free, MIT licensed, no email.

Browse them with previews and one-click copy at **[kuan-ai.com/skills](https://kuan-ai.com/skills?utm_source=github&utm_medium=readme&utm_campaign=skills-repo)**.

## Install

All skills into `~/.claude/skills`:

```sh
curl -fsSL https://kuan-ai.com/skills/install | sh
```

Only some of them, or into the current project (`./.claude/skills`):

```sh
curl -fsSL https://kuan-ai.com/skills/install | sh -s code-review
curl -fsSL https://kuan-ai.com/skills/install | sh -s -- --project code-review
```

Or clone this repo and copy any folder from `skills/` into your skills folder. Restart Claude Code and ask for the task normally: the agent picks the skill from its description.

## Skills

| Skill | Category | What it does | |
|---|---|---|---|
| [Code review](skills/code-review/SKILL.md) | Coding | Reviews a diff for bugs it has verified in the code, ranks them by severity and gives a failing scenario and minimal fix for each. | [page](https://kuan-ai.com/skills/code-review?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Commit messages](skills/commit-message/SKILL.md) | Coding | Writes a commit message that matches the repo's conventions and explains why, then commits safely without skipping hooks or staging secrets. | [page](https://kuan-ai.com/skills/commit-message?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Pull request description](skills/pr-description/SKILL.md) | Coding | Writes a PR title and description from the real diff, filling the repo's template, with test steps you actually ran and risks called out. | [page](https://kuan-ai.com/skills/pr-description?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Write unit tests](skills/write-tests/SKILL.md) | Coding | Writes tests in the project's own framework, proves each one fails when the behavior breaks, and reports bugs instead of encoding them. | [page](https://kuan-ai.com/skills/write-tests?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Systematic debugging](skills/debug-detective/SKILL.md) | Coding | Finds the root cause of a bug by reproducing it, narrowing with evidence and bisecting, then fixes the cause with a regression test. | [page](https://kuan-ai.com/skills/debug-detective?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Safe refactoring](skills/refactor-safely/SKILL.md) | Coding | Restructures code in small verified steps that keep tests, types and public behavior intact, and flags any change that is not a pure refactor. | [page](https://kuan-ai.com/skills/refactor-safely?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [README writer](skills/readme-writer/SKILL.md) | Coding | Writes or updates a README with commands verified against the repo, real env vars and setup steps that get a newcomer running fast. | [page](https://kuan-ai.com/skills/readme-writer?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [SQL helper](skills/sql-helper/SKILL.md) | Coding | Writes, checks and speeds up SQL against your real schema, catching NULL and join fan-out bugs and guarding every write with a preview and transaction. | [page](https://kuan-ai.com/skills/sql-helper?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [API documentation](skills/api-docs/SKILL.md) | Coding | Documents HTTP endpoints by tracing routes, middleware and validators in the code, so params, auth and error codes match what the server really does. | [page](https://kuan-ai.com/skills/api-docs?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Dockerize an app](skills/dockerize/SKILL.md) | Coding | Adds a Dockerfile, .dockerignore and compose file matched to your stack, then builds and runs the container to prove it starts and responds. | [page](https://kuan-ai.com/skills/dockerize?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Changelog from commits](skills/changelog/SKILL.md) | Coding | Turns a git range into user-facing release notes with breaking changes and migration steps first, each item traceable to its commit or PR. | [page](https://kuan-ai.com/skills/changelog?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Security check](skills/security-check/SKILL.md) | Coding | Finds exploitable security bugs in a repo or diff by tracing user input to dangerous sinks, ranked by real risk with file:line and a fix. | [page](https://kuan-ai.com/skills/security-check?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Meeting notes](skills/meeting-notes/SKILL.md) | Productivity | Turns a transcript into decisions, action items with owner and date, and open questions, without inventing owners, dates or agreements. | [page](https://kuan-ai.com/skills/meeting-notes?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Email replies](skills/email-replier/SKILL.md) | Writing | Drafts email replies that answer every question in order, never commit you to anything you did not approve, and mark missing facts as placeholders. | [page](https://kuan-ai.com/skills/email-replier?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [SEO article writer](skills/seo-article/SKILL.md) | Marketing | Writes a search-intent-matched article that answers the query first, adds original substance, and never invents statistics, sources or links. | [page](https://kuan-ai.com/skills/seo-article?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Research brief](skills/research-brief/SKILL.md) | Research | Researches a question with primary sources, a clear stop rule and exact citations, and returns a short brief that says what is known, disputed and unknown. | [page](https://kuan-ai.com/skills/research-brief?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Competitor analysis](skills/competitor-analysis/SKILL.md) | Business | Compares competitors on audience, price, features and real customer complaints, with a source and date for every cell, and finds the gap you can own. | [page](https://kuan-ai.com/skills/competitor-analysis?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Spreadsheet / CSV analyst](skills/data-analyst/SKILL.md) | Research | Analyzes a CSV or spreadsheet with code, checks data quality and reconciles totals, and answers with verified numbers, caveats and the findings that matter. | [page](https://kuan-ai.com/skills/data-analyst?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Product spec (PRD)](skills/product-spec/SKILL.md) | Business | Turns a feature idea into a one-page spec with problem, scope, acceptance criteria, edge cases and a measurable goal, marking every assumption. | [page](https://kuan-ai.com/skills/product-spec?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Customer support reply](skills/support-reply/SKILL.md) | Business | Drafts support replies that fix the issue within your policies, never claim actions not taken, and flag tickets that need a human or escalation. | [page](https://kuan-ai.com/skills/support-reply?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |

## Prompts

| Prompt | Category | What it does | |
|---|---|---|---|
| [Rewrite in plain language](prompts/rewrite-plainly.md) | Writing | Rewrites dense text so a non-expert gets it on first read, keeping every fact and flagging any sentence whose meaning was unclear. | [page](https://kuan-ai.com/skills/rewrite-plainly?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Shorten a text](prompts/shorten-text.md) | Writing | Cuts a text to a word target while keeping the point, the key facts and the author's voice, then reports exactly what was removed. | [page](https://kuan-ai.com/skills/shorten-text?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Change the tone](prompts/tone-shifter.md) | Writing | Rewrites a message in a new tone (firmer, warmer, more formal, more casual) without changing its requests or facts, in two lengths. | [page](https://kuan-ai.com/skills/tone-shifter?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [LinkedIn post from an experience](prompts/linkedin-post.md) | Writing | Turns something you did or learned into a specific, non-cringe LinkedIn post using only your real details, with 3 hooks to pick from. | [page](https://kuan-ai.com/skills/linkedin-post?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [X (Twitter) thread](prompts/x-thread.md) | Writing | Turns an article or notes into an X thread where every post stands alone, fits the limit and uses only facts from your content. | [page](https://kuan-ai.com/skills/x-thread?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Cold email that gets replies](prompts/cold-email.md) | Writing | Writes a short cold email built on real research about the prospect, with a low-effort ask and two follow-ups that each add something new. | [page](https://kuan-ai.com/skills/cold-email?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Newsletter issue](prompts/newsletter-issue.md) | Writing | Builds a full newsletter issue from your notes and links: 5 subject lines, a main story with a clear action, quick hits and no invented facts. | [page](https://kuan-ai.com/skills/newsletter-issue?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Explain it from zero](prompts/explain-like-new.md) | Research | Learn any topic from your current knowledge: plain definition, an analogy and where it breaks, key ideas, a worked example and a self-test. | [page](https://kuan-ai.com/skills/explain-like-new?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Steelman both sides](prompts/steelman.md) | Research | Lays out the strongest case for and against a question, the shared facts and the real crux, with what evidence would settle it. | [page](https://kuan-ai.com/skills/steelman?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Summarize a paper or long report](prompts/summarize-paper.md) | Research | Extracts a paper's claim, method, real numbers and weak spots, checks whether the evidence backs the headline, all from the text only. | [page](https://kuan-ai.com/skills/summarize-paper?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Fact-check a text](prompts/fact-check.md) | Research | Pulls every checkable claim out of a text, rates each with a reason and the source that would settle it, worst problems first. | [page](https://kuan-ai.com/skills/fact-check?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [30-day learning plan](prompts/learning-plan.md) | Research | A realistic 30-day plan to learn a skill: one concrete task a day, a weekly project, checkpoints and what to cut if you fall behind. | [page](https://kuan-ai.com/skills/learning-plan?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Explain this code](prompts/explain-code.md) | Coding | Understand unfamiliar code fast: purpose, step-by-step flow, side effects, hidden assumptions and likely bugs, without rewriting it. | [page](https://kuan-ai.com/skills/explain-code?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Regex builder](prompts/regex-builder.md) | Coding | Builds a regex from match and no-match examples, explains every part and checks each example in a test table before answering. | [page](https://kuan-ai.com/skills/regex-builder?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Decode an error message](prompts/error-decoder.md) | Coding | Explains an error or stack trace in plain words, points at the line that matters, and ranks the likely causes with a check and a fix for each. | [page](https://kuan-ai.com/skills/error-decoder?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Name it well](prompts/naming-helper.md) | Coding | Names for functions, variables, tables or tools that say what the thing does, follow your conventions and don't clash with existing names. | [page](https://kuan-ai.com/skills/naming-helper?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Shell one-liner](prompts/shell-one-liner.md) | Coding | A safe, copy-ready shell command for your OS, with a dry run for anything destructive and a breakdown of each part. | [page](https://kuan-ai.com/skills/shell-one-liner?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Translate code to another language](prompts/translate-code.md) | Coding | Ports code to another language idiomatically, keeps behavior identical, flags what can't map 1:1 and adds tests that prove it. | [page](https://kuan-ai.com/skills/translate-code?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Landing page copy](prompts/landing-page-copy.md) | Marketing | Full landing page copy built from your customer's problem and only the proof you give it: no hype, no invented numbers. | [page](https://kuan-ai.com/skills/landing-page-copy?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [10 headlines, 5 angles](prompts/headlines.md) | Marketing | 10 headlines across 5 testable angles, within your character limit, using only facts you supply: no invented numbers or clickbait. | [page](https://kuan-ai.com/skills/headlines?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [SEO topic cluster](prompts/seo-keyword-cluster.md) | Marketing | Plans a pillar page and 12-15 supporting articles by search intent, without made-up search volumes, ready to check in your keyword tool. | [page](https://kuan-ai.com/skills/seo-keyword-cluster?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Product description that sells](prompts/product-description.md) | Marketing | E-commerce product copy with benefits first, scannable specs, SEO title and meta, built only from the details you give it. | [page](https://kuan-ai.com/skills/product-description?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Ad copy variants](prompts/ad-copy-variants.md) | Marketing | Ad copy for Meta, Google Search or LinkedIn within real character limits, in 5 testable angles, with no invented proof or fake urgency. | [page](https://kuan-ai.com/skills/ad-copy-variants?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Customer persona from real data](prompts/customer-persona.md) | Marketing | Builds a persona from the reviews, interviews or tickets you paste, with quotes as evidence and 'unknown' instead of stereotypes. | [page](https://kuan-ai.com/skills/customer-persona?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Pricing tiers](prompts/pricing-page.md) | Business | Designs 2-3 pricing tiers tied to a value metric, with margins from your real costs and cheap experiments to validate them. | [page](https://kuan-ai.com/skills/pricing-page?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Honest SWOT](prompts/swot.md) | Business | A SWOT ranked by impact, with facts separated from assumptions, that ends in the 3 actions to take this quarter. | [page](https://kuan-ai.com/skills/swot?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Negotiation reply](prompts/negotiation-reply.md) | Business | Answers an offer, discount request or late payer firmly, with a trade for every concession and your walk-away point kept hidden. | [page](https://kuan-ai.com/skills/negotiation-reply?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Job description people finish reading](prompts/job-description.md) | Business | A job post about the real work, first-90-day projects and honest requirements, with salary shown and no clichés or invented perks. | [page](https://kuan-ai.com/skills/job-description?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Plan my week](prompts/weekly-plan.md) | Productivity | Turns a messy task list into a realistic week: priorities, time estimates with buffer, focus blocks and what to drop. | [page](https://kuan-ai.com/skills/weekly-plan?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Decision matrix](prompts/decision-matrix.md) | Productivity | Compares options on weighted criteria, tests whether the winner survives other weights, and runs a pre-mortem before you commit. | [page](https://kuan-ai.com/skills/decision-matrix?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |

## More from KuanAI

- [AI agents explained, guides and comparisons](https://kuan-ai.com/blog?utm_source=github&utm_medium=readme&utm_campaign=skills-repo)
- [Free AI tools](https://kuan-ai.com/tools?utm_source=github&utm_medium=readme&utm_campaign=skills-repo)
- [Store: agent templates and kits](https://kuan-ai.com/store?utm_source=github&utm_medium=readme&utm_campaign=skills-repo)
- X: [@KuanAIDev](https://x.com/KuanAIDev)

Contributions welcome: open an issue or a PR with a new skill (one folder, one `SKILL.md` with `name` and `description` in the front matter).

![](https://prospector.tailc67124.ts.net:10000/p/github-kuanai-skills-repo-readme)
