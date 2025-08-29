---
include: "*.sql"
title: Do not rename tables
tags: postgresql,prisma,supabase,mysql,drizzle,migrations
---

When renaming tables, use a multi-step approach instead of direct renaming to prevent downtime.

1. Create a new table
2. Write to both tables
3. Backfill data from the old table to the new table
4. Move reads from the old table to the new table
5. Stop writing to the old table
6. Drop the old table

Bad:

```sql
ALTER TABLE users RENAME TO customers;
```
