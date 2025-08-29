---
include: "*.go"
title: Early returns in Go
tags: golang
---

Use early returns to reduce nesting levels. Prefer checking error conditions or guard clauses first and returning early, rather than wrapping the main logic in deep conditional blocks.

Bad:

```go
func processData(data []string) (string, error) {
    if len(data) > 0 {
        if isValid(data) {
            result := ""
            for _, item := range data {
                if item != "" {
                    // More nested code here
                    result += transform(item)
                }
            }
            return result, nil
        } else {
            return "", errors.New("invalid data")
        }
    } else {
        return "", errors.New("empty data")
    }
}
```

Good:

```go
func processData(data []string) (string, error) {
    if len(data) == 0 {
        return "", errors.New("empty data")
    }

    if !isValid(data) {
        return "", errors.New("invalid data")
    }

    result := ""
    for _, item := range data {
        if item == "" {
            continue
        }
        result += transform(item)
    }

    return result, nil
}
```
