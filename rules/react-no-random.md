---
include: "*.tsx"
title: No random numbers in React
tags: nextjs,react,typescript
---

Do not generate non-deterministic values like random IDs during render in React components. This causes hydration errors because the server-rendered HTML will not match what the client generates.

Avoid using functions like `Math.random()`, `Date.now()`, `uuid()`, or any other source of randomness directly in your render function or JSX.

Instead:

- Generate IDs in useEffect hooks
- Use stable IDs based on props or state
- Use refs to store generated values
- Use libraries that support SSR (like uuid with specific configuration)

Bad:

```tsx
function UserCard() {
  // This will generate different values on server and client
  const id = `user-${Math.random()}`

  return (
    <div id={id}>
      <input aria-labelledby={`label-${Math.floor(Math.random() * 1000)}`} />
    </div>
  )
}
```

Good:

```tsx
function UserCard({ userId }) {
  // Using stable props for IDs
  const id = `user-${userId}`

  // For dynamic IDs, use useEffect and useState
  const [randomId, setRandomId] = useState(null)

  useEffect(() => {
    // Generate random values after mounting
    setRandomId(`label-${Math.floor(Math.random() * 1000)}`)
  }, [])

  return <div id={id}>{randomId && <input aria-labelledby={randomId} />}</div>
}
```
