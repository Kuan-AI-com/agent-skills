---
name: migration-safety
description: Write or review a database schema migration so it runs on a live system without downtime or data loss. Use when the user adds, renames or drops a column or table, adds an index or constraint, changes a type, backfills data, or asks "is this migration safe?".
---

# Safe database migrations

A migration is safe when every step works while old and new app versions run at the same time, and every step can be stopped or undone.

## 1. Gather the facts first

- Database and version (Postgres, MySQL, SQLite...), the migration tool (Prisma, Rails, Alembic, Flyway, Knex, Django...) and how migrations run in deploys (before, during or after the new code goes live).
- Table sizes and write traffic for every table touched. If you cannot see them, ask, or write the plan for "large and busy" and say so.
- Who reads and writes these columns: grep the code, background jobs, reports, other services. A column is not unused just because this repo does not mention it.

## 2. Classify each operation

Usually safe: add a nullable column without a volatile default, create a table, add an index concurrently (`CREATE INDEX CONCURRENTLY` in Postgres; `ALGORITHM=INPLACE, LOCK=NONE` in MySQL where supported).

Dangerous on a live table, so split it up:
- Rename or drop a column or table: old code still uses it.
- Change a column type: often rewrites the table under a lock.
- Add `NOT NULL` or a foreign key to existing data: full scan under lock. In Postgres, add the constraint `NOT VALID`, then `VALIDATE CONSTRAINT` separately.
- Add a plain index on a big table: blocks writes.
- Backfill in one `UPDATE`: long transaction, lock pile-up, replication lag.

## 3. Use expand / contract

1. **Expand:** add the new column or table. Nothing reads it yet.
2. **Dual write:** deploy code that writes both old and new.
3. **Backfill:** in batches (for example 1,000-10,000 rows per transaction, keyed by primary key), resumable, with a short pause between batches. Watch locks and replica lag.
4. **Switch reads** to the new column. Verify counts and samples match.
5. **Contract:** stop writing the old one, wait at least one deploy, then drop it in a separate migration.

Each step is its own migration and its own deploy. Never combine a destructive step with the code change that makes it possible.

## 4. Protect the database

- Set a `lock_timeout` (for example 5s) and `statement_timeout` on migration sessions, so a blocked migration fails fast instead of queueing every query behind it. Retry with backoff.
- Migrations that cannot run inside a transaction (`CONCURRENTLY`) must be marked as such in the tool.
- Test on a copy with production-like size when you can, and time it.

## 5. Plan the rollback

For every step, write how to undo it and whether undoing loses data. A dropped column cannot be rolled back: take a backup or keep the data elsewhere first.

## Do not

- Run anything against production yourself. Hand over the commands.
- Edit a migration that has already run anywhere. Write a new one.
- Claim a step is non-blocking without naming the database version where that holds.

## Output

1. Risk summary: each operation, lock taken, estimated impact (or "unknown: table size not given").
2. The step-by-step plan with the migration files and the code change for each deploy.
3. Backfill script, if any.
4. Rollback for each step.
5. Checks to run after each step (queries that prove it worked).
