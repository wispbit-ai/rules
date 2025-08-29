---
include: "*.go"
title: Use structured logger in Go
tags: golang
---

Use the structured logger for all logging operations instead of fmt.Print or log package functions.

Bad:

```go
import (
    "fmt"
    "log"
)

func processOrder(order Order) error {
    fmt.Println("Processing order:", order.ID)

    if err := validateOrder(order); err != nil {
        log.Printf("Error validating order %s: %v", order.ID, err)
        return err
    }

    return nil
}
```

Good:

```go
import (
    "github.com/yourproject/logger"
)

func processOrder(order Order) error {
    logger.Info("Processing order", "orderID", order.ID)

    if err := validateOrder(order); err != nil {
        logger.Error("Failed to validate order", "orderID", order.ID, "error", err)
        return err
    }

    return nil
}
```
