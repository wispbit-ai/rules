---
include: "*.go"
title: Avoid unnecessary else blocks in Go
tags: golang
---

Avoid unnecessary `else` blocks when the `if` block ends with a return statement, break, continue, or similar control flow statements.

Bad:

```go
func processValue(value int) string {
    if value > 10 {
        return "high"
    } else {
        return "low"
    }
}
```

```go
func checkItems(items []string) {
    for _, item := range items {
        if len(item) > 5 {
            fmt.Println("Long item:", item)
            continue
        } else {
            fmt.Println("Short item:", item)
        }
    }
}
```

Good:

```go
func processValue(value int) string {
    if value > 10 {
        return "high"
    }
    return "low"
}
```

```go
func checkItems(items []string) {
    for _, item := range items {
        if len(item) > 5 {
            fmt.Println("Long item:", item)
            continue
        }
        fmt.Println("Short item:", item)
    }
}
```
