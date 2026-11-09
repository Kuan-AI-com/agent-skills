---
name: dockerize
description: Containerize an existing project with a production-ready Dockerfile, .dockerignore and docker-compose.yml, then build and run it to verify. Use when the user says "dockerize this", "add a Dockerfile", "run this in Docker", "containerize the app", or "docker-compose for local dev".
---

# Dockerize an app

## 1. Detect the stack

- Language and runtime version: `.nvmrc`, `engines`, `.python-version`, `pyproject.toml`, `go.mod`, `Gemfile`, `.tool-versions`. Use the same major version in the base image.
- Package manager from the lockfile (npm, pnpm, yarn, poetry, uv, pip). No lockfile: tell the user builds will not be reproducible.
- Build and start commands from `package.json` scripts, `Procfile`, `Makefile`, or the framework.
- Port, and the env vars the app needs (`.env.example`, config reads in code).
- Services it talks to: database, cache, queue, object storage.
- If a Dockerfile already exists, improve it instead of replacing it.

## 2. Dockerfile

- Official base image with a pinned version tag (`node:22-bookworm-slim`, `python:3.12-slim`). Avoid `latest`. Prefer Debian slim over Alpine unless the user wants Alpine: musl breaks some native packages and prebuilt binaries (Prisma, sharp, many Python wheels).
- Multi-stage: dependencies and build in one stage, copy only runtime artifacts into the final stage.
- Copy lockfile and manifest first, install, then copy source, so the install layer caches.
- Reproducible installs: `npm ci`, `pnpm install --frozen-lockfile`, `yarn install --immutable`, `pip install --no-cache-dir -r requirements.txt`, `uv sync --frozen`. Production-only dependencies in the final stage.
- Framework specifics: Next.js with `output: "standalone"`; Python with `PYTHONUNBUFFERED=1`; compiled Go/Rust into a minimal or distroless image.
- Run as a non-root user (the `node` user in node images, or create one).
- Exec-form `CMD ["node", "server.js"]` so the process gets SIGTERM and shuts down cleanly. Avoid `npm start` as PID 1; it may not forward signals.
- The app must listen on `0.0.0.0`, not `localhost`/`127.0.0.1`, or it will be unreachable from outside the container. Check the code and set `HOST` if needed.
- `HEALTHCHECK` only if there is a health endpoint and a tool to call it exists in the image (slim images have no `curl`; use the runtime itself, e.g. `node -e "fetch(...)"`).
- No secrets in `ARG`, `ENV` or copied files; they stay in image layers. Pass them at runtime.

## 3. .dockerignore

`.git`, `node_modules`, virtualenvs, build output, `.env*` (keep `.env.example` only if needed), logs, coverage, local DB files, OS files. Without it, the build context leaks secrets and busts the cache.

## 4. docker-compose.yml

- The app plus the real dependencies it needs locally, using official images with pinned versions.
- Named volumes for data, `env_file: .env` for config, ports mapped explicitly.
- `depends_on` with `condition: service_healthy` and a healthcheck on the database, so the app does not start before it is ready.
- Inside compose, the app reaches the DB at the service name (`db:5432`), not `localhost`. Point the connection string there.
- Database migrations: a separate one-off command or service, not baked into the image build.

## 5. Build, run, verify

```
docker build -t <app> .
docker compose up -d
docker compose ps
docker compose logs app --tail 50
curl -i http://localhost:<port>/<health-or-root>
docker image ls <app>
```
Fix and rebuild until the container starts, stays up and responds. Report the final image size.

If the user builds on Apple Silicon and deploys to x86 servers, mention `docker build --platform linux/amd64`.

## Report

Files created, commands to build and run, env vars the user must set, and anything you could not verify (for example, services you could not start locally).
