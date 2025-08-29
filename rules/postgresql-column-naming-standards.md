---
include: "*.sql"
title: Column naming standards in PostgreSQL
tags: postgresql,prisma,supabase,drizzle,migrations
---

Maintain consistent naming conventions for new columns.

Bad

```sql
-- Bad: Column named uuid instead of id
ALTER TABLE users ADD COLUMN uuid UUID PRIMARY KEY DEFAULT gen_random_uuid();
```

```sql
-- Bad: Column named camelCase instead of snake_case
ALTER TABLE users ADD COLUMN firstName VARCHAR(255);
```

```sql
-- Bad: Column foreign key ends with uuid instead of id
ALTER TABLE orders ADD COLUMN user_uuid UUID REFERENCES users(id);
```

## Good

```sql
-- Good: Consistent naming
ALTER TABLE users ADD COLUMN id UUID PRIMARY KEY DEFAULT gen_random_uuid();
ALTER TABLE users ADD COLUMN first_name VARCHAR(255);
ALTER TABLE orders ADD COLUMN user_id UUID REFERENCES users(uuid);
```
