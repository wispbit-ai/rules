---
include: "*.spec.ts,*.test.ts"
title: Annotate skipped tests in Typescript
tags: typescript
---

When skipping tests, always add a comment explaining why the test is being skipped.

Bad:

```typescript
describe.skip("enqueueExecution", () => {
  // test code
})
```

Good:

```typescript
// Test was skipped because it was flaky
describe.skip("enqueueExecution", () => {
  // test code
})
```
