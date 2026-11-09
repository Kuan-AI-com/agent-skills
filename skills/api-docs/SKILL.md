---
name: api-docs
description: Write reference documentation or an OpenAPI spec for a REST/HTTP API by reading its source code. Use when the user says "document the API", "write endpoint docs", "generate an OpenAPI/Swagger spec", "what endpoints do we have", or "document this route".
---

# API documentation

Document what the code does, not what the endpoint name suggests. Anything you could not confirm is marked as such.

## 1. Check for existing specs or generators

Look for `openapi.*`, `swagger.*`, FastAPI (serves `/openapi.json`), NestJS `@nestjs/swagger`, `drf-spectacular`, `springdoc`, tRPC/GraphQL schemas, or zod-to-openapi. If the framework can generate the spec, prefer configuring that over writing one by hand, and say so.

## 2. Find every route

Use the framework's convention, then confirm by searching:
- Express/Fastify/Koa: `app.get(`, `router.post(`, mounted prefixes from `app.use('/prefix', router)`.
- Next.js: `app/**/route.ts` (exported `GET`, `POST`...) and `pages/api/**`.
- FastAPI/Flask/Django: `@app.get`, `@router.post`, `@bp.route`, `urls.py`.
- Rails `config/routes.rb`, Laravel `routes/*.php`, Go `HandleFunc`/router groups, Spring `@GetMapping`.
Build the full path including prefixes and versioning. List the endpoints first and ask if internal or admin ones should be included.

## 3. For each endpoint, trace the handler

- **Auth**: follow the middleware chain, decorators or guards. Note the mechanism (bearer token, session cookie, API key header) and any role or ownership check.
- **Input**: path params, query params, headers and body from the validator (zod, joi, pydantic, class-validator, serializers). Copy exact types, required/optional, defaults, enums, min/max, formats.
- **Responses**: every status the handler returns or throws, plus framework defaults (validation errors are often 400 or 422, unauthenticated 401, unhandled 500). Take the response shape from the code or the response model.
- **Side effects** worth knowing: sends email, charges a card, is not idempotent, rate limited.

## 4. Write it

For Markdown docs, per endpoint:

```
### POST /api/v1/orders
Creates an order for the current user.

Auth: Bearer token, role "customer".

| Field | In | Type | Required | Notes |
|---|---|---|---|---|

Responses:
- 201: { example JSON with realistic values }
- 400: validation error, example body
- 401, 404 ...

Example:
curl -X POST http://localhost:3000/api/v1/orders -H "Authorization: Bearer $TOKEN" -H "Content-Type: application/json" -d '{"sku":"A1","qty":2}'
```

Group endpoints by resource. Put shared things (base URL, auth, error format, pagination) once at the top.

For OpenAPI: version 3.1 YAML (3.0 if the user's tooling needs it), reusable `components/schemas` for shared shapes, `securitySchemes` for auth, an `operationId` per operation.

## 5. Verify

- If you can run the server locally, call a couple of endpoints with the curl examples and correct any mismatch.
- Validate an OpenAPI file with a linter if one is available (for example `npx @redocly/cli lint openapi.yaml`); otherwise at least check it parses as YAML.
- Mark anything inferred with "(unverified)" and list those points in your reply.

## Do not

- Invent endpoints, fields, status codes or rate limits.
- Put real tokens, keys or customer data in examples.
