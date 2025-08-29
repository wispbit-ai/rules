---
include: "*.go"
title: Structured logging in Go
tags: golang
---

Always use structured logging with field-based approaches instead of string formatting when logging in Go.

Bad:

```go
logger.Info(fmt.Sprintf("User %s logged in from IP %s with status %d", username, ipAddress, statusCode))
```

Good:

```go
logger.Info("User authentication",
    "username", username,
    "ip", ipAddress,
    "status", statusCode,
)
```
