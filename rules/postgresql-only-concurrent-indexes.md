---
include: "*.sql"
title: Only concurrent indexes in PostgreSQL
tags: postgresql,prisma,supabase,drizzle,migrations
---

When creating indexes in PostgreSQL, always use the `CONCURRENTLY` option to prevent blocking writes during index creation.

Bad:

```sql
CREATE INDEX idx_users_email ON users(email);
```

Good:

```sql
CREATE INDEX CONCURRENTLY idx_users_email ON users(email);
```
