---
name: security-check
description: Review a codebase, pull request or diff for exploitable security problems. Use when the user asks for a security review or audit, "is this safe", "check for vulnerabilities", "any secrets leaked?", or before deploying or open-sourcing a project.
---

# Security check

## 1. Scope first
- A diff/PR: review only changed code plus whatever it calls or exposes. A whole repo: start from entry points (routes, handlers, CLI, queue consumers, webhooks).
- Note the stack, the framework's built-in protections (ORM parameterization, template auto-escaping, CSRF middleware) and where auth is enforced. Many "findings" are already handled by the framework: check before reporting.

## 2. Secrets
- Search working tree: `git grep -nIE '(api[_-]?key|secret|token|passwd|password|BEGIN [A-Z ]*PRIVATE KEY)'` and known prefixes (`sk_live_`, `AKIA`, `ghp_`, `xox`).
- History: `git log -p -S '<suspect string>'` or `git log --all --diff-filter=D --name-only` for deleted .env files. Use gitleaks/trufflehog only if installed.
- Check .gitignore covers `.env*`, keys, dumps.
- **Never print a full secret.** Show the first 4 characters and the location. A secret that ever reached git history must be rotated, not just deleted: say so.

## 3. Trace input to sinks
For each entry point, follow untrusted input (body, query, headers, cookies, filenames, webhook payloads, LLM output) to:
- SQL/NoSQL built by string concatenation; shell commands (`exec`, `system`, `subprocess(shell=True)`); `eval`/dynamic imports
- file paths (path traversal, `../`), uploads (type, size, storage location, served back as HTML?)
- outbound URLs fetched by the server (SSRF to 169.254.169.254, localhost)
- HTML/markdown rendered without escaping (XSS), redirects to user-given URLs
- deserialization of untrusted data (pickle, YAML load, Java serialization)
Report only when you can name the path from source to sink. If you cannot confirm it, list it as "to verify", not as a finding.

## 4. Authorization
- Every endpoint that reads or changes data: who may call it? Look for IDs from the request used without an ownership check (IDOR), admin routes guarded only in the UI, mass assignment (`role`, `isAdmin` accepted from the body).
- Webhooks: signature verified? Password reset and login: rate limited, tokens single-use and expiring?

## 5. Config and dependencies
- Debug mode or verbose errors in production, `CORS *` with credentials, cookies missing HttpOnly/Secure/SameSite, missing security headers on HTML apps.
- Run the ecosystem audit if available (`npm audit --omit=dev`, `pip-audit`, `cargo audit`, `govulncheck`). Report only vulnerable packages that are reachable in production; ignore dev-only and unreachable advisories.
- Logs that write tokens, passwords or personal data.

## 6. Report
Rank by severity: **Critical** (remote, no auth, data or account takeover), **High**, **Medium**, **Low**. For each:
- file:line, one-sentence issue
- how an attacker uses it (concrete request or input)
- the fix (code-level, minimal)

Then: **To verify** (suspicions without a confirmed path) and **Not checked** (areas out of scope or not readable). No theoretical padding: if you found nothing critical, say so plainly.

Do not modify code unless asked. Do not run exploits against live or third-party systems.
