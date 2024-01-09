---
date: 2024-01-09T09:19:48+01:00
title: 'pg_rman: a backup and restore management tool for PostgreSQL'
tags: ["links", "postgres"]
---
> The goal of the pg_rman project is to provide a method for online backup and
PITR that is as easy as pg_dump. Also, it maintains a backup catalog per
database cluster. Users can maintain old backups including archive logs with one
command.

We've always been doing our Postgres backups the rudimentary way via
`pg_dumpall`, which works and is purely logical (one can restore across different
Postgres versions), but `pg_rman` maintains a catalog and has point-in-time
recovery. 

I might want to [look into it](https://github.com/ossc-db/pg_rman) at some point.