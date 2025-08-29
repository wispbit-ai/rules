---
include: "*.spec.ts,*.test.ts"
title: Avoid console.log in Typescript tests
tags: typescript
---

Avoid using `console.log` statements in test files.

Bad:

```typescript
describe("Example test", () => {
  it("should test something", () => {
    const result = someFunction()
    console.log(result) // Debugging statement left in the code
    expect(result).toBe(expectedValue)
  })
})
```

Good:

```typescript
describe("Example test", () => {
  it("should test something", () => {
    const result = someFunction()
    expect(result).toBe(expectedValue)
  })
})
```
