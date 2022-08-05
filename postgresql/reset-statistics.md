## Reset statistics

You can reset the pg_stat_statements by calling the `pg_stat_statements_reset()` function:

```
tetsuya-connect-playground::DATABASE=> SELECT pg_stat_statements_reset();
 pg_stat_statements_reset
--------------------------

(1 row)
```

For a Heroku Postgres database, you can use `pg:outliers --reset` or `pg:stats-reset` command instead. See [How to I reset the statistics for a Heroku Postgres database?](https://help.heroku.com/NF3K4865/how-to-i-reset-the-statistics-for-a-heroku-postgres-database) for more detials.

Note that these counters are reset by some events:

> When recovery is performed at server start (e.g., after immediate shutdown, server crash, and point-in-time recovery), all statistics counters are reset.
> [27.2.1. Statistics Collection Configuration](https://www.postgresql.org/docs/13/monitoring-stats.html#MONITORING-STATS-SETUP)
