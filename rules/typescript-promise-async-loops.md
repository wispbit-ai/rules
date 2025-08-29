---
include: "*.ts"
title: Promise all async loops in Typescript
tags: typescript
---

Use `Promise.all` when processing multiple async operations in loops.

Bad:

```typescript
async function processItems(items: string[]) {
  const results = []

  for (const item of items) {
    // Sequential execution - slower
    const result = await fetchData(item)
    results.push(result)
  }

  return results
}
```

Good:

```typescript
async function processItems(items: string[]) {
  // Parallel execution - faster
  const results = await Promise.all(
    items.map(async (item) => {
      return await fetchData(item)
    })
  )

  return results
}
```
