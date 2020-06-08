# PostgreSQL
## \dn
Lists schemas

```
tetsuya-connect-playground::DATABASE=> \dn
       List of schemas
    Name    |     Owner
------------+----------------
 public     | u8cebnm6oom3e3
 salesforce | u8cebnm6oom3e3
(2 rows)
```

## \dt
Lists tables

```
tetsuya-connect-playground::DATABASE=> \dt public.*;
                   List of relations
 Schema |         Name         | Type  |     Owner
--------+----------------------+-------+----------------
 public | ar_internal_metadata | table | u8cebnm6oom3e3
 public | schema_migrations    | table | u8cebnm6oom3e3
 public | users                | table | u8cebnm6oom3e3
(3 rows)
```

## \d
Shows table structure

```
tetsuya-connect-playground::DATABASE=> \d public.users;
                                          Table "public.users"
   Column   |              Type              | Collation | Nullable |              Default
------------+--------------------------------+-----------+----------+-----------------------------------
 id         | bigint                         |           | not null | nextval('users_id_seq'::regclass)
 name       | character varying              |           |          |
 email      | character varying              |           |          |
 created_at | timestamp(6) without time zone |           | not null |
 updated_at | timestamp(6) without time zone |           | not null |
Indexes:
    "users_pkey" PRIMARY KEY, btree (id)
```
