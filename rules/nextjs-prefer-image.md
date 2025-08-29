---
include: "*.tsx"
title: Prefer Image in NextJS
tags: nextjs
---

Always use Next.js `<Image>` component instead of HTML `<img>` tag.

Bad:

```jsx
function ProfileCard() {
  return (
    <div className="card">
      <img src="/profile.jpg" alt="User profile" width={200} height={200} />
      <h2>User Name</h2>
    </div>
  )
}
```

Good:

```jsx
import Image from "next/image"

function ProfileCard() {
  return (
    <div className="card">
      <Image
        src="/profile.jpg"
        alt="User profile"
        width={200}
        height={200}
        priority={false}
      />
      <h2>User Name</h2>
    </div>
  )
}
```
