---
include: "*.ts"
title: HTTP conventions in Express API endpoints
tags: typescript,expressjs
---

Ensure that for any new endpoint, the status code is matched with the correct purpose:

- Use `401 Unauthorized` for authentication failures (when credentials are missing or invalid)
- Use `403 Forbidden` for authorization failures (when user is authenticated but lacks required permissions)
- Use `404 Not Found` for resources that don't exist
- Use `400 Bad Request` for invalid request parameters
- Use `500 Internal Server Error` for server-side errors

Bad:

```typescript
// Wrong status code for permission error
app.get("/resource", (req: Request, res: Response) => {
  if (!req.user) {
    return res.status(401).json({ error: "Permission denied" })
  }

  if (!hasPermission(req.user, "read_resource")) {
    return res.status(401).json({ error: "Permission denied" }) // Wrong code
  }

  // Resource handling...
})
```

Good:

```typescript
// Correct status codes for different scenarios
app.get("/resource", (req: Request, res: Response) => {
  if (!req.user) {
    return res.status(401).json({ error: "Authentication required" })
  }

  if (!hasPermission(req.user, "read_resource")) {
    return res.status(403).json({ error: "Permission denied" }) // Correct code
  }

  // Resource handling...
})
```
