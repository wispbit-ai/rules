---
include: "*.ts,*.tsx"
title: Avoid duplicate words in Typescript
tags: typescript,react
---

Check all text elements (comments, docstrings, and string literals) for duplicate adjacent words for typos or duplicates.

Bad:

```typescript
// This function validates the the input parameters
function validateInput() {
    ...
}
```

Good:

```typescript
// This function validates the input parameters
function validateInput() {
    ...
}
```
