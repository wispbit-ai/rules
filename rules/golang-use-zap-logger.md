---
include: "*.go"
title: Use Zap logger in Go
tags: golang
---

Use Zap for all logging in Go code.

Bad:

```go
func processOrder(order Order) error {
    fmt.Printf("Processing order %s\n", order.ID)

    if err := validateOrder(order); err != nil {
        log.Printf("Error validating order: %v", err)
        return err
    }

    fmt.Println("Order processed successfully")
    return nil
}
```

Good:

```go
func processOrder(order Order) error {
    logger := zap.L().With(zap.String("orderID", order.ID))
    logger.Info("Processing order")

    if err := validateOrder(order); err != nil {
        logger.Error("Failed to validate order", zap.Error(err))
        return err
    }

    logger.Info("Order processed successfully")
    return nil
}
```
