# Learning Plan State

Updated by Stage 1 of `/learn-daily-generate`; persists across runs.

## Database and Postgres (`topic_e84b1e30`, priority 1)

User preference: generic DB concept first, then Postgres specifics. Do NOT
make the user memorise sizes (page size, header bytes, etc.) — structure is
fine, numbers are not.

**Covered (run_2026-10-25, fundamentals tier):** pages as the unit of I/O;
buffer pool / shared buffers & dirty pages; key vs constraint vs index;
primary key (+ auto unique B-tree index); foreign key (no auto index on
referencing side); B-tree basics; index write overhead; WAL rule; why WAL is
cheap; checkpoints & crash recovery.

**Next (intermediate tier), roughly in order:**
1. Page structure at a conceptual level (line pointers → tuples, TID/ctid) — no sizes.
2. MVCC: UPDATE/DELETE leave dead tuples → why VACUUM exists.
3. HOT updates and how extra indexes prevent them.
4. Insert path cost per object: unique-index check, FK lookup on referenced
   table, CHECK/NOT NULL cost (CPU), index page splits.
5. How objects get created: CREATE INDEX (scan + sort + build), locking,
   CREATE INDEX CONCURRENTLY, ADD CONSTRAINT ... NOT VALID + VALIDATE.
6. WAL extras: full-page writes after checkpoint, WAL & replication/PITR.
