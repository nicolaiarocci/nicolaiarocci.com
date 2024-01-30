---
date: 2024-01-30T15:56:15+01:00
title: pg_dump and pg_restore can backup and restore single Postgres schemas
tags: ["til", "postgres"]
---
Today I learned that `pg_dump` can make a copy of a Postgres schema instead of
the whole database. Likewise, if needed, `pg_restore` can restore the schema in
either the original database or a different one.

Backup of a Postgres schema:

```
pg_dump -h host -d source_database -U user -n schema_name -F c -f schema_dump_file.dump
```

Restore of a Postgres schema:

```
pg_restore -h host -d dest_database -U user -n schema_name schema_dump_file.dump
```

All primary and shared knowledge, I am sure. Another item of note: the DB name
is hard-coded in `pg_dumpall` files, so if one wants to restore on a database
named differently, one must go into the dump file and edit it by hand. 