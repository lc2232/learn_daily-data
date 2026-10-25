# Learning Plan State

Updated by Stage 1 of `/learn-daily-generate`; persists across runs.

## Postgres Internals (`topic_b1a9dca5`, priority 1)

**Covered (run_2026-10-25):** pages (size, layout, ctid/line pointers);
keys vs constraints vs indexes (PK, UNIQUE, FK indexing, NULL distinctness);
vacuum/analyze foundations (dead tuples, VACUUM vs FULL, ANALYZE, visibility map).

**Outstanding — pick up next run, roughly in this order:**
1. Write path with indexes/constraints enabled — heap insert, index inserts per
   index, uniqueness check, FK check, WAL; HOT updates (no index change + room on page).
2. COPY FROM vs INSERT vs UPSERT (`INSERT ... ON CONFLICT`) — per-row overhead,
   batching, conflict arbiter index requirements.
3. What happens internally on CREATE INDEX / ADD CONSTRAINT / ADD PRIMARY KEY —
   locks taken, CREATE INDEX CONCURRENTLY, `NOT VALID` + `VALIDATE CONSTRAINT`.
4. Deeper vacuum: XID wraparound/freezing, autovacuum thresholds — if not covered.
