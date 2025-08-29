---
include: "*.sql"
title: Add indexes for foreign keys in PostgreSQL
tags: postgresql,prisma,supabase,drizzle,migrations
---

When adding a foreign key constraint in PostgreSQL, always add a corresponding index.

Bad:

```sql
ALTER TABLE orders
ADD CONSTRAINT fk_orders_user_id
FOREIGN KEY (user_id) REFERENCES users(id);
```

Good:

```sql
ALTER TABLE orders
ADD CONSTRAINT fk_orders_user_id
FOREIGN KEY (user_id) REFERENCES users(id);
CREATE INDEX CONCURRENTLY idx_orders_user_id ON orders (user_id);
```
