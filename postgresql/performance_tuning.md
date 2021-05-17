## EXPLAIN ANALYZE
Statement will be executed. Do not use on an `INSERT`, `UPDATE`, `DELETE` ect. without `ROLLBACK`.

see: [PostgreSQL: Documentation: 13: EXPLAIN](https://www.postgresql.org/docs/current/sql-explain.html)

## VACUUM vs VACUUM FULL
* Tuple - row
* Bloat - storage occupied by dead (soft deleted) tuples
* `VACUUM` - removes bloat but primarily marks the space available for future reuse.
* `VACUUM FULL` - compacts tables by re-writing a table. The space used by dead tuples will be returned to the operating system.

see: [24.1.2. Recovering Disk Space](https://www.postgresql.org/docs/13/routine-vacuuming.html#VACUUM-FOR-SPACE-RECOVERY)
