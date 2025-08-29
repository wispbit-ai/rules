---
include: "*.tsx"
title: No unused components
tags: nextjs,react,typescript
---

Do not leave commented-out components. Either remove unused components entirely or implement them properly.

Bad:

```tsx
function MyComponent() {
  return (
    <div>
      <Header />
      {/* <Sidebar>
        <Navigation />
      </Sidebar> */}
      <MainContent />
    </div>
  )
}
```

Good:

```tsx
function MyComponent() {
  return (
    <div>
      <Header />
      <MainContent />
    </div>
  )
}
```
