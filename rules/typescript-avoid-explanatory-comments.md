---
include: "*.ts,*.tsx"
title: Self documenting code in Typescript
tags: typescript
---

Avoid unnecessary explanatory comments for code that is self-documenting. Comments should only be used when they add context that the code itself cannot convey.

Bad:

```typescript
// Use the test-specific directory path
testDir = join(BASE_DIR, testCase.identifier)
```

Good:

```typescript
testDir = join(BASE_DIR, testCase.identifier)
```
