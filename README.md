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
| [Code review](skills/code-review/SKILL.md) | Coding | Reviews a diff for real bugs first, style last, and reports each finding with a concrete failure case. | [page](https://kuan-ai.com/skills/code-review?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Commit messages](skills/commit-message/SKILL.md) | Coding | Writes clear commit messages from the staged diff: a short subject that says why, and a body only when it helps. | [page](https://kuan-ai.com/skills/commit-message?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Pull request description](skills/pr-description/SKILL.md) | Coding | Turns a branch into a PR description reviewers can read in one minute: what, why, how to test, risks. | [page](https://kuan-ai.com/skills/pr-description?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Write unit tests](skills/write-tests/SKILL.md) | Coding | Writes tests that catch real regressions, using the project's own framework and conventions. | [page](https://kuan-ai.com/skills/write-tests?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Systematic debugging](skills/debug-detective/SKILL.md) | Coding | Finds the root cause of a bug with hypotheses and evidence instead of random edits. | [page](https://kuan-ai.com/skills/debug-detective?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Safe refactoring](skills/refactor-safely/SKILL.md) | Coding | Refactors in small steps that keep tests green, without changing behavior. | [page](https://kuan-ai.com/skills/refactor-safely?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [README writer](skills/readme-writer/SKILL.md) | Coding | Writes a README that gets a new developer from clone to running in five minutes. | [page](https://kuan-ai.com/skills/readme-writer?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [SQL helper](skills/sql-helper/SKILL.md) | Coding | Writes and explains SQL against your real schema, with safe defaults for updates and deletes. | [page](https://kuan-ai.com/skills/sql-helper?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [API documentation](skills/api-docs/SKILL.md) | Coding | Documents HTTP endpoints from the code: parameters, responses, errors and a curl example for each. | [page](https://kuan-ai.com/skills/api-docs?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Dockerize an app](skills/dockerize/SKILL.md) | Coding | Creates a small, secure Dockerfile and docker-compose.yml for an existing project. | [page](https://kuan-ai.com/skills/dockerize?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Changelog from commits](skills/changelog/SKILL.md) | Coding | Turns git history into a changelog people want to read, grouped by what changed for them. | [page](https://kuan-ai.com/skills/changelog?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Security check](skills/security-check/SKILL.md) | Coding | Scans a project for the most common real-world security mistakes and ranks them by risk. | [page](https://kuan-ai.com/skills/security-check?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Meeting notes](skills/meeting-notes/SKILL.md) | Productivity | Turns a transcript into decisions, action items with owners and dates, and open questions. | [page](https://kuan-ai.com/skills/meeting-notes?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Email replies](skills/email-replier/SKILL.md) | Writing | Drafts replies that answer every question, match the sender's tone and end with a clear next step. | [page](https://kuan-ai.com/skills/email-replier?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [SEO article writer](skills/seo-article/SKILL.md) | Marketing | Plans and writes a search-friendly article that answers the query in the first paragraph. | [page](https://kuan-ai.com/skills/seo-article?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Research brief](skills/research-brief/SKILL.md) | Research | Researches a question and returns a sourced brief that separates facts, estimates and opinions. | [page](https://kuan-ai.com/skills/research-brief?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Competitor analysis](skills/competitor-analysis/SKILL.md) | Business | Compares competitors on price, features, audience and positioning, and finds the gap you can own. | [page](https://kuan-ai.com/skills/competitor-analysis?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Spreadsheet / CSV analyst](skills/data-analyst/SKILL.md) | Research | Explores a CSV or spreadsheet, checks data quality and answers questions with numbers and charts. | [page](https://kuan-ai.com/skills/data-analyst?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Product spec (PRD)](skills/product-spec/SKILL.md) | Business | Turns an idea into a one-page spec: problem, users, scope, success metric and what is out of scope. | [page](https://kuan-ai.com/skills/product-spec?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Customer support reply](skills/support-reply/SKILL.md) | Business | Answers customer tickets with empathy and a concrete fix, following your policies. | [page](https://kuan-ai.com/skills/support-reply?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |

## Prompts

| Prompt | Category | What it does | |
|---|---|---|---|
| [Rewrite in plain language](prompts/rewrite-plainly.md) | Writing | Makes any text clear for a non-expert without losing meaning. | [page](https://kuan-ai.com/skills/rewrite-plainly?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Cut it in half](prompts/shorten-text.md) | Writing | Shortens a text to a target length while keeping the point and the voice. | [page](https://kuan-ai.com/skills/shorten-text?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Change the tone](prompts/tone-shifter.md) | Writing | Rewrites a message in a different tone: firmer, warmer, more formal or more casual. | [page](https://kuan-ai.com/skills/tone-shifter?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [LinkedIn post from an experience](prompts/linkedin-post.md) | Writing | Turns something you did or learned into a LinkedIn post that is specific, not cringe. | [page](https://kuan-ai.com/skills/linkedin-post?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [X (Twitter) thread](prompts/x-thread.md) | Writing | Turns an article, idea or notes into a thread where every post stands on its own. | [page](https://kuan-ai.com/skills/x-thread?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Cold email that gets replies](prompts/cold-email.md) | Writing | A short, specific first email to a prospect, plus two follow-ups. | [page](https://kuan-ai.com/skills/cold-email?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Newsletter issue](prompts/newsletter-issue.md) | Writing | Builds a newsletter issue from your links and notes, with a strong subject line. | [page](https://kuan-ai.com/skills/newsletter-issue?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Explain it from zero](prompts/explain-like-new.md) | Research | Learn any topic with an analogy, the key ideas and a quick self-test. | [page](https://kuan-ai.com/skills/explain-like-new?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Steelman both sides](prompts/steelman.md) | Research | Gets the strongest version of each side of a debate before you decide. | [page](https://kuan-ai.com/skills/steelman?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Summarize a paper or long report](prompts/summarize-paper.md) | Research | Extracts the claim, the method, the evidence and the weak spots of a paper. | [page](https://kuan-ai.com/skills/summarize-paper?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Fact-check a text](prompts/fact-check.md) | Research | Lists every checkable claim in a text and rates how much to trust each one. | [page](https://kuan-ai.com/skills/fact-check?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [30-day learning plan](prompts/learning-plan.md) | Research | A realistic day-by-day plan to learn a skill with projects, not just reading. | [page](https://kuan-ai.com/skills/learning-plan?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Explain this code](prompts/explain-code.md) | Coding | Understand unfamiliar code fast: purpose, flow, gotchas. | [page](https://kuan-ai.com/skills/explain-code?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Regex builder](prompts/regex-builder.md) | Coding | Builds a regular expression from examples and explains every part. | [page](https://kuan-ai.com/skills/regex-builder?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Decode an error message](prompts/error-decoder.md) | Coding | Explains an error or stack trace in plain words and gives the likely fixes in order. | [page](https://kuan-ai.com/skills/error-decoder?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Name it well](prompts/naming-helper.md) | Coding | Clear names for variables, functions, files, products or companies. | [page](https://kuan-ai.com/skills/naming-helper?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Shell one-liner](prompts/shell-one-liner.md) | Coding | Gets a safe shell command for a task, explained piece by piece. | [page](https://kuan-ai.com/skills/shell-one-liner?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Translate code to another language](prompts/translate-code.md) | Coding | Ports code to another language idiomatically, not line by line. | [page](https://kuan-ai.com/skills/translate-code?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Landing page copy](prompts/landing-page-copy.md) | Marketing | Full landing page copy built from your customer's problem, not your feature list. | [page](https://kuan-ai.com/skills/landing-page-copy?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [10 headlines, 5 angles](prompts/headlines.md) | Marketing | Headline variants for an article, ad or page, using different angles to test. | [page](https://kuan-ai.com/skills/headlines?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [SEO topic cluster](prompts/seo-keyword-cluster.md) | Marketing | Plans a pillar page and supporting articles around one topic. | [page](https://kuan-ai.com/skills/seo-keyword-cluster?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Product description that sells](prompts/product-description.md) | Marketing | E-commerce product copy: benefits first, scannable specs, SEO title. | [page](https://kuan-ai.com/skills/product-description?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Ad copy variants](prompts/ad-copy-variants.md) | Marketing | Ad copy for Meta, Google or LinkedIn in the right lengths, ready to A/B test. | [page](https://kuan-ai.com/skills/ad-copy-variants?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Customer persona from real data](prompts/customer-persona.md) | Marketing | Builds a useful persona from reviews, interviews or support tickets you paste. | [page](https://kuan-ai.com/skills/customer-persona?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Pricing tiers](prompts/pricing-page.md) | Business | Designs 2-3 pricing tiers with clear value jumps and the reasoning behind them. | [page](https://kuan-ai.com/skills/pricing-page?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Honest SWOT](prompts/swot.md) | Business | A SWOT analysis that leads to actions instead of a pretty grid. | [page](https://kuan-ai.com/skills/swot?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Negotiation reply](prompts/negotiation-reply.md) | Business | Responds to an offer, discount request or late payer firmly without burning the relationship. | [page](https://kuan-ai.com/skills/negotiation-reply?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Job description people finish reading](prompts/job-description.md) | Business | A job post focused on the work and the outcomes, with honest requirements. | [page](https://kuan-ai.com/skills/job-description?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Plan my week](prompts/weekly-plan.md) | Productivity | Turns a messy task list into a realistic week with priorities and time blocks. | [page](https://kuan-ai.com/skills/weekly-plan?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |
| [Decision matrix](prompts/decision-matrix.md) | Productivity | Compares options on weighted criteria and checks the decision with a pre-mortem. | [page](https://kuan-ai.com/skills/decision-matrix?utm_source=github&utm_medium=readme&utm_campaign=skills-repo) |

## More from KuanAI

- [AI agents explained, guides and comparisons](https://kuan-ai.com/blog?utm_source=github&utm_medium=readme&utm_campaign=skills-repo)
- [Free AI tools](https://kuan-ai.com/tools?utm_source=github&utm_medium=readme&utm_campaign=skills-repo)
- [Store: agent templates and kits](https://kuan-ai.com/store?utm_source=github&utm_medium=readme&utm_campaign=skills-repo)
- X: [@KuanAIDev](https://x.com/KuanAIDev)

Contributions welcome: open an issue or a PR with a new skill (one folder, one `SKILL.md` with `name` and `description` in the front matter).

![](https://prospector.tailc67124.ts.net:10000/p/github-kuanai-skills-repo-readme)
