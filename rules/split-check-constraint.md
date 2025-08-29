---
include: "*.sql"
title: Split check constraints
tags: postgresql,prisma,supabase,mysql,drizzle,migrations
---

When adding check constraints in migrations, split the operation into two steps to avoid blocking writes during the table scan:

1. First create the check constraint without validation
2. Then validate existing data in a separate migration

Bad:

```sql
-- In a single migration
ALTER TABLE users ADD CONSTRAINT ck_users_age_positive
CHECK (age >= 0);
```

Good:

```sql
-- In first migration: add without validating
ALTER TABLE users ADD CONSTRAINT ck_users_age_positive
CHECK (age >= 0)
NOT VALID;

-- In second migration: validate existing data
ALTER TABLE users VALIDATE CONSTRAINT ck_users_age_positive;
```
