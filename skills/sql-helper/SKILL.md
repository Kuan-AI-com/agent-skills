---
name: sql-helper
description: Write, fix, explain or speed up SQL queries and schema changes against the project's real database schema. Use when the user asks for "a query that...", "a report from the database", "why is this query slow", "add an index", "update/delete these rows", or pastes SQL that returns wrong numbers.
---

# SQL helper

## 1. Know the database and schema

- Dialect: from the connection string, driver or ORM config (`DATABASE_URL`, `prisma/schema.prisma` provider, `settings.py`, `knexfile`, `docker-compose.yml` image). Postgres, MySQL/MariaDB, SQLite and SQL Server differ in upserts, date functions, string concat, `LIMIT`/`TOP` and identifier quoting.
- Schema: migrations or ORM models in the repo; otherwise ask the user to run `\d table` (psql), `SHOW CREATE TABLE t` (MySQL) or `.schema t` (SQLite). Never guess column names, types or which columns are nullable.
- Ask about row counts for big tables when performance matters.

## 2. Write the query

- Explicit column list, readable aliases, one join per line with its condition.
- In application code, use the driver's parameter placeholders. Never build SQL by concatenating user input.
- State any assumption about the data ("assumes one active subscription per user").

## 3. Check correctness traps

Before handing over, check each one that applies:
- **Join fan-out**: joining a one-to-many table before `SUM`/`COUNT` multiplies rows. Aggregate in a subquery or CTE first, then join.
- **NULLs**: `col = NULL` is never true; `NOT IN (subquery)` returns nothing if the subquery has a NULL (use `NOT EXISTS`); `COUNT(col)` skips NULLs, `COUNT(*)` does not; `LEFT JOIN` + a `WHERE` on the right table turns it into an inner join (move the filter into `ON`).
- **Grouping**: every non-aggregated selected column is in `GROUP BY`.
- **Ordering**: `LIMIT`/pagination without a unique `ORDER BY` gives unstable results.
- **Dates**: time zones of stored timestamps, inclusive vs exclusive ranges (prefer `>= start AND < next_day`), integer division in ratios.
- **Duplicates**: does the user want distinct entities or all rows?

## 4. Writes (UPDATE, DELETE, INSERT ... SELECT)

- First give a `SELECT COUNT(*)` and a sample `SELECT` with the exact same `WHERE`, and ask the user to confirm the count.
- Wrap in a transaction; check the affected row count before `COMMIT`.
- Large tables: batch by primary key ranges to avoid long locks and replication lag.
- Do not run writes against production yourself unless the user explicitly asks; hand them the SQL.

## 5. Slow queries

- Get the plan: `EXPLAIN` (safe) or `EXPLAIN ANALYZE` (Postgres/MySQL 8). `EXPLAIN ANALYZE` executes the query: never use it on a write outside a transaction you roll back.
- Look for: full scans on large tables, functions or casts on indexed columns (`WHERE lower(email) = ...`), leading-wildcard `LIKE '%x'`, sorts or hashes spilling to disk, N+1 queries coming from the app.
- Index suggestions must name the exact columns and order (equality filters first, then range, then sort), and note the write cost. On Postgres production tables use `CREATE INDEX CONCURRENTLY`; on MySQL check the online DDL behavior for the version.
- Re-run the plan after the change and compare.

## Output

The SQL in a code block, then 2-4 lines: what it returns (what one row means), assumptions, and any trap you guarded against. For schema changes, also give the rollback statement.
