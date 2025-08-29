---
include: "*.ts,*.tsx"
title: Always return empty arrays in Typescript
tags: typescript,react
---

When defining methods that return collections like arrays, always return an empty array instead of undefined when no items exist.

Bad:

```typescript
function getUserNames(): string[] | undefined {
  if (users.length === 0) {
    return undefined
  }
  return users.map((user) => user.name)
}
```

Good:

```typescript
function getUserNames(): string[] {
  if (users.length === 0) {
    return []
  }
  return users.map((user) => user.name)
}
```
