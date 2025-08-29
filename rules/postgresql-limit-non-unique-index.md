---
include: "*.sql"
title: Limit non unique indexes in PostgreSQL
tags: postgresql,prisma,supabase,drizzle,migrations
---

Limit non-unique indexes to a maximum of three columns in PostgreSQL databases:

Bad:

```sql
CREATE INDEX index_users_on_multiple_columns ON users (column_a, column_b, column_c, column_d);
```

Good:

```sql
CREATE INDEX CONCURRENTLY index_users_on_selective_columns ON users (column_d, column_b);
```
