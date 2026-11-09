---
name: readme-writer
description: Write a new README or update an outdated one for a project, with setup, configuration and usage that match the actual code. Use when the user says "write a README", "document how to run this", "update the README", "setup instructions", or "onboarding docs".
---

# README writer

Every command, file name and env var in the README must exist in the repo. A wrong quick start is worse than none.

## 1. Collect facts from the repo

- What it is: entry points, `package.json` description, existing docs, the main routes or CLI commands.
- Runtime and versions: `.nvmrc`, `.node-version`, `engines`, `.python-version`, `pyproject.toml`, `go.mod`, `.tool-versions`, Dockerfile base image.
- Package manager from the lockfile: `package-lock.json` npm, `pnpm-lock.yaml` pnpm, `yarn.lock` yarn, `bun.lockb` bun, `poetry.lock` poetry, `uv.lock` uv.
- Commands: scripts in `package.json`, `Makefile` targets, `justfile`, `Taskfile`, CI workflows (they show the real build and test order).
- Configuration: `.env.example`, plus a search for where config is read (`process.env.`, `os.environ`, `os.Getenv`, `config(`). Mark which ones the app cannot start without.
- External services: database, queue, cache, third-party APIs, and how they are started locally (docker-compose?).
- License: only from a `LICENSE` file.

## 2. Updating an existing README

Keep the author's structure and any sections you cannot verify (mark them for the user to check instead of deleting). Fix outdated commands, add what is missing, and tell the user what you changed.

## 3. Structure

1. **Name + one sentence**: what it does and for whom. Then, if useful, 2-3 bullets of what it can do. No hype.
2. **Quick start**: prerequisites with versions, then copy-paste commands from clone to a running app, ending with how to see it works (URL, expected output).
3. **Configuration**: table of env vars: name, required, example value, what it does. Placeholders only, never real values.
4. **Common tasks**: test, lint, build, migrate, deploy, each with its exact command.
5. **Project layout**: only the folders a newcomer needs to find, one line each.
6. **Troubleshooting**: only real problems (from issues, comments in code, or ones you hit while verifying).
7. Contributing and license, if the repo has them.

Drop any section that would be empty or speculative. A small library may need only sections 1, 2 and 4 plus a usage example.

## 4. Verify

- Run the quick start and common task commands if the environment allows it (skip deploys and anything touching production). Fix the README or tell the user when a command fails.
- Commands you could not run: say so in your reply, not in the README.
- Check that every relative link and file path in the README exists.

## Do not

- Invent features, badges, benchmarks, support channels or a roadmap.
- Paste secrets, internal hostnames or personal data found in config files.
- Duplicate long reference docs; link to them.
