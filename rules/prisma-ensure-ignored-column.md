---
include: "*.sql"
title: Ensure removed column is ignored in Prisma
tags: postgresql,prisma,migrations
---

When creating a migration to remove a column from the database, ensure that the schema has the `@ignore` attribute on that column in the Prisma schema. Search for the .prisma schema in the codebase to verify this.

```sql
ALTER TABLE "User" DROP COLUMN "createdAt";
ALTER TABLE "User" DROP COLUMN "updatedAt";
```

```prisma
model User {
  id        Int       @id @default(autoincrement())
  email     String    @unique
  password  String
  remarks   String?
  createdAt DateTime  @default(now()) @ignore
  updatedAt DateTime  @updatedAt @ignore
}
```
