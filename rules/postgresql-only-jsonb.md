---
include: "*.sql"
title: Always use JSONB in PostgreSQL
tags: postgresql,prisma,supabase,drizzle,migrations
---

Always use `jsonb` instead of `json` data type when creating columns in PostgreSQL databases.

Bad:

```sql
ALTER TABLE users
ADD COLUMN properties json;
```

Good:

```sql
ALTER TABLE users
ADD COLUMN properties jsonb;
```
