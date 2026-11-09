---
name: sql-helper
description: Write, explain or optimize SQL queries. Use when the user asks for a query, a report from a database, or why a query is slow.
---

# SQL helper

1. Get the schema first: migrations, ORM models, or `\d table` / `SHOW CREATE TABLE`. Never guess column names.
2. Ask which database (Postgres, MySQL, SQLite...) if it is not clear; syntax differs.
3. Write the query with explicit column lists, readable aliases and comments for non-obvious joins.
4. For UPDATE or DELETE: always show a SELECT with the same WHERE first, and wrap the change in a transaction.
5. For slow queries: read the EXPLAIN plan, look for sequential scans on large tables, functions on indexed columns and N+1 patterns, then suggest a specific index.
6. Explain the result in plain words: what each row means.
