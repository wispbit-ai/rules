---
include: "*.sql"
title: Use check constraints for setting NOT NULL columns in PostgreSQL
tags: postgresql,prisma,supabase,drizzle,migrations
---

When adding a NOT NULL constraint to an existing column in PostgreSQL, use a check constraint first to avoid blocking reads and writes while every row is checked.

Bad:

```sql
-- This can cause performance issues with large tables
ALTER TABLE users
ALTER COLUMN some_column SET NOT NULL;
```

Good:

```sql
-- Step 1: Add a check constraint without validation
ALTER TABLE users
ADD CONSTRAINT users_some_column_null CHECK (some_column IS NOT NULL) NOT VALID;

-- Step 2: In a separate transaction, validate the constraint
ALTER TABLE users
VALIDATE CONSTRAINT users_some_column_null;

-- Step 3: Add the NOT NULL constraint and remove the check constraint
ALTER TABLE users
ALTER COLUMN some_column SET NOT NULL;

ALTER TABLE users
DROP CONSTRAINT users_some_column_null;
```
