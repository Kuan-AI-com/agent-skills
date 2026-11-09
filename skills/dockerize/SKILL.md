---
name: dockerize
description: Add Docker support to a project: Dockerfile, .dockerignore and docker-compose.yml. Use when the user asks to containerize or dockerize an app.
---

# Dockerize an app

1. Detect the stack and its start command from the repo (package.json scripts, requirements, go.mod...).
2. Dockerfile:
   - official slim base image pinned to a major version
   - multi-stage build: install and build in one stage, copy only the output to the final stage
   - copy dependency manifests first so layers cache
   - run as a non-root user
   - EXPOSE the real port and a HEALTHCHECK if there is a health endpoint
3. .dockerignore: node_modules, .git, .env*, build output, logs.
4. docker-compose.yml: the app plus its real dependencies (database, cache) with named volumes and an env_file. Never bake secrets into the image.
5. Give the commands to build and run, and check the image size.
