---
include: "*.ts"
title: Avoid duplicate assignment in Typescript
tags: typescript
---

Avoid assigning values to the same variable multiple times in succession without using the variable in between.

Bad:

```typescript
let count = 0
count = 1 // Duplicate assignment without using the initial value
count = 2 // Another duplicate assignment
```

Good:

```typescript
let count = 2 // Direct assignment to final value
```
