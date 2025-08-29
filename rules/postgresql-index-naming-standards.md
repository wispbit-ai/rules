---
include: "*.sql"
title: Index naming standards in PostgreSQL
tags: postgresql,prisma,supabase,drizzle,migrations
---

For indexes, use the following naming standards:

- `idx_tablename_columnname` for single column indexes,
- `idx_tablename_col1_col2` for multi-column indexes

## Bad

```sql
-- Bad: Inconsistent and unclear index names
CREATE INDEX email_index ON users(email);
CREATE INDEX user_orders ON orders(user_id);
CREATE INDEX idx_prod_cat_stat ON products(category, status);
```

## Good

```sql
-- Good: Consistent index naming
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_orders_user_id ON orders(user_id);
CREATE INDEX idx_products_category_status ON products(category, status);
```
