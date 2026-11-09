---
name: readme-writer
description: Write or update a project README. Use when the user asks for a README, setup docs or project documentation.
---

# README writer

Read package.json / pyproject / Makefile / Dockerfile and the entry points before writing. Every command in the README must exist in the repo.

Structure:
1. **Name and one sentence**: what it does and for whom.
2. **Quick start**: prerequisites with versions, then copy-paste commands from clone to running.
3. **Configuration**: environment variables in a table (name, required, example, meaning). Never include real secret values.
4. **Common tasks**: test, build, deploy, lint.
5. **Project layout**: only the folders a newcomer needs.
6. **Troubleshooting**: the errors people actually hit.

Short sentences. No marketing language. Test the quick start commands if you can run them.
