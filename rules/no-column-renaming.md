---
include: "*.sql"
title: Do not rename columns
tags: postgresql,prisma,supabase,mysql,drizzle,migrations
---

When renaming columns in PostgreSQL, follow a safe migration pattern to avoid breaking changes to applications:

1. Create a new column
2. Update application code to write to both the old and new columns
3. Backfill data from the old column to the new column
4. Update application code to read from the new column instead of the old one
5. Once all deployments are complete, stop writing to the old column
6. Drop the old column in a later migration

Bad:

```sql
ALTER TABLE users RENAME COLUMN some_column TO new_name;
```
