---
include: "*.go"
title: Avoid getter methods in Go
tags: golang
---

Avoid using "getter" methods in Go code. Instead, expose fields directly when appropriate, following Go's idiomatic approach to visibility.

Bad:

```go
type Person struct {
    name string
    age  int
}

func (p *Person) GetName() string {
    return p.name
}

func (p *Person) GetAge() int {
    return p.age
}

// Usage
name := person.GetName()
```

Good:

```go
type Person struct {
    Name string
    Age  int
}

// Usage
name := person.Name
```
