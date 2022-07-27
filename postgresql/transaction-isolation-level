## Check transaction isolation level for your database

```
tetsuya-connect-playground::DATABASE=> SELECT name, setting FROM pg_settings WHERE name = 'default_transaction_isolation';
-[ RECORD 1 ]--------------------------
name    | default_transaction_isolation
setting | read committed
```

For each Isolation Level, 
[PostgreSQL: Documentation: 14: 13.2. Transaction Isolation](https://www.postgresql.org/docs/current/transaction-iso.html)
