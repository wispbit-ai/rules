---
include: "*.sql"
title: Always have id, created_at, updated_at columns in PostgreSQL
tags: postgresql,prisma,supabase,drizzle,migrations
---

All CREATE TABLE statements must include `id`, `created_at`, and `updated_at` columns.

Bad:

```sql
CREATE TABLE users (
    email VARCHAR(255) NOT NULL UNIQUE,
    name VARCHAR(100) NOT NULL
);
```

Good:

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) NOT NULL UNIQUE,
    name VARCHAR(100) NOT NULL,
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW() NOT NULL,
    updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW() NOT NULL
);
```
