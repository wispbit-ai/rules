---
include: "*.ts"
title: Consistent error classes in Typescript
tags: typescript
---

Use consistent naming conventions for error classes.

Bad:

```typescript
abstract class PublicAPiError extends Error {
  // Inconsistent casing in "APi" - should be either "Api" or "API"
}

class UnauthorizedHTtpError extends Error {
  // Inconsistent casing in "HTtp" - should be either "Http" or "HTTP"
}
```

Good:

```typescript
abstract class PublicApiError extends Error {
  // Consistent Pascal casing with "Api"
}

class UnauthorizedHttpError extends Error {
  // Consistent Pascal casing with "Http"
}

// Or alternatively:

abstract class PublicAPIError extends Error {
  // Consistent uppercase for the acronym "API"
}

class UnauthorizedHTTPError extends Error {
  // Consistent uppercase for the acronym "HTTP"
}
```
