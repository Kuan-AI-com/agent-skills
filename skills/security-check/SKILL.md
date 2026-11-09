---
name: security-check
description: Check a codebase or change for common security problems. Use when the user asks for a security review, audit or "is this safe".
---

# Security check

Look for, in this order:
1. **Secrets** committed in code, config or git history (API keys, passwords, private keys). Check .gitignore covers .env files.
2. **Injection**: user input reaching SQL strings, shell commands, eval, file paths or HTML without escaping.
3. **Auth**: endpoints that change data without checking the user, IDs taken from the request without ownership checks (IDOR).
4. **Dependencies**: run the ecosystem's audit (npm audit, pip-audit) and report only exploitable, production dependencies.
5. **Config**: debug mode in production, permissive CORS, missing rate limits on login and forms, cookies without HttpOnly/Secure.
6. **Data**: logs that print tokens or personal data.

Report each issue with file:line, how an attacker would use it, and the fix. Rank by real risk. Do not pad the report with theoretical issues.
