---
include: "*.vue, *.ts, *.js"
title: Validate redirect URLs
tags: vue,typescript
---

Always validate redirect URLs to prevent open redirect vulnerabilities. When validating external URLs, parse them with the URL constructor and compare origins exactly rather than using string operations.

Bad:

```javascript
// Vulnerable to subdomain attacks (e.g., example.com.attacker.com)
const isRedirectSafe = (redirectUrl) => {
  return (
    redirectUrl.startsWith("/") ||
    redirectUrl.startsWith(window.location.origin)
  )
}
```

Good:

```javascript
const isRedirectSafe = (redirectUrl) => {
  // Allow local redirects
  if (redirectUrl.startsWith("/")) {
    return true
  }

  try {
    // Validate external URLs by checking exact origin match
    const url = new URL(redirectUrl)
    return url.origin === window.location.origin
  } catch {
    return false
  }
}
```
