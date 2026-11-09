---
name: api-docs
description: Document a REST or HTTP API from its source code. Use when the user asks for API docs, endpoint docs or an OpenAPI description.
---

# API documentation

For each endpoint found in the routes:

### METHOD /path
One sentence: what it does.

- **Auth**: required or not, and how (header, cookie).
- **Parameters**: path, query and body fields in a table: name, type, required, description, example.
- **Responses**: each status code the code can return, with an example JSON body.
- **Errors**: validation and permission errors with their messages.
- **Example**: a curl command that works against a local server.

Read the validation code (zod, pydantic, etc.) to get exact types and limits. Do not document endpoints that do not exist. If the user wants OpenAPI, output valid OpenAPI 3.1 YAML.
