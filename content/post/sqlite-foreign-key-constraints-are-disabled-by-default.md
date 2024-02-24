---
date: 2024-02-22T17:35:40+01:00
title: SQLite foreign key constraints are disabled by default
tags: ["til", "sqlite"]
---
Today, I learned that SQLite only enforces foreign-key constraints if explicitly
instructed. I imagine this is well-known and trivial for the SQLite initiated,
but we're a Postgres shop; I have used SQLite sporadically, primarily for
experiments like today's, and this one amenity was certainly unexpected.

Anyways. I had all my `ON DELETE CASCADE` constraints nicely configured, but
related records in child tables were not being deleted when I deleted the
parent. Perplexed, I [looked it up](https://www.sqlite.org/foreignkeys.html). 

> Foreign key constraints are disabled by default (for backwards compatibility),
so must be enabled separately for each database connection. 

The quick fix was to add `"foreign keys=true;"` to our connection string.
Alternatively, the application can also use a `PRAGMA foreign keys = ON;`
statement to activate them once the connection is established, but it doesn't
make sense, as we need constraints active throughout the connection's lifecycle.