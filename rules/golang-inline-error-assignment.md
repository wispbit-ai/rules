---
include: "*.go"
title: Inline error assignment in Go
tags: golang
---

Use inline error assignment with the `:=` operator when checking for errors.

Bad:

```go
var err error
result, err = someFunction()
if err != nil {
    return err
}
```

Good:

```go
if result, err := someFunction(); err != nil {
    return err
}
```
