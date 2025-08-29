---
include: "*.tsx"
title: Check for duplicate components
tags: nextjs,react,typescript
---

Favor existing components over creating new ones.

Before creating a new component, check if an existing component can satisfy the requirements through its props and parameters.

Bad:

```tsx
// Creating a new component that duplicates functionality
export function FormattedDate({ date, variant }) {
  // Implementation that duplicates existing functionality
  return <span>{/* formatted date */}</span>
}
```

Good:

```tsx
// Using an existing component with appropriate parameters
import { DateTime } from "./DateTime"

function Page() {
  return <DateTime date={date} variant={variant} noTrigger={true} />
}
```
