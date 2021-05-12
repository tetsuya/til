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

## \x
Turn on the expanded table formatting mode

```
tetsuya-connect-playground::DATABASE=> select * from users limit 1;
 id |    name     |       email       |         created_at         |         updated_at
----+-------------+-------------------+----------------------------+----------------------------
  1 | test user 1 | test1@example.com | 2020-06-25 18:31:03.557066 | 2020-06-25 18:31:03.557066
(1 row)

tetsuya-connect-playground::DATABASE=> \x
tetsuya-connect-playground::DATABASE=> select * from users limit 1;
-[ RECORD 1 ]--------------------------
id         | 1
name       | test user 1
email      | test1@example.com
created_at | 2020-06-25 18:31:03.557066
updated_at | 2020-06-25 18:31:03.557066
```
