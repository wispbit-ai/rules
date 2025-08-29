---
include: "*.py"
title: No unused code in python
tags: python
---

Do not leave commented-out code blocks in Python files. If code is no longer needed, remove it entirely rather than commenting it out.

Bad:

```python
def calculate_total(items):
    total = 0
    for item in items:
        total += item.price

    # Old calculation method that we might need later
    # subtotal = 0
    # for item in items:
    #     if item.type != 'tax':
    #         subtotal += item.price
    # tax = calculate_tax(subtotal)
    # total = subtotal + tax

    return total
```

Good:

```python
def calculate_total(items):
    total = 0
    for item in items:
        total += item.price

    return total
```
