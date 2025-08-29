---
include: "*.sql"
title: Split foreign keys in PostgreSQL
tags: postgresql,prisma,supabase,drizzle,migrations
---

When adding foreign keys in Postgres migrations, split the operation into two steps to avoid blocking writes on both tables:

1. First create the foreign key constraint without validation
2. Then validate existing data in a separate migration

Bad:

```sql
-- In a single migration
ALTER TABLE users ADD CONSTRAINT fk_users_orders
FOREIGN KEY (order_id) REFERENCES orders (id);
```

Good:

```sql
-- In first migration: add without validating
ALTER TABLE users ADD CONSTRAINT fk_users_orders
FOREIGN KEY (order_id) REFERENCES orders (id)
NOT VALID;

-- In second migration: validate existing data
ALTER TABLE users VALIDATE CONSTRAINT fk_users_orders;
```
