---
include: "*.py"
title: Avoid duplicate variable reassignment in Python
tags: python
---

Avoid assigning a variable to itself or reassigning a variable with the same value.

Bad:

```python
# Redundant self-assignment
x = 10
x = x  # Unnecessary reassignment

# Duplicate assignment with the same value
y = "hello"
# ... some code ...
y = "hello"  # Unnecessary reassignment with identical value
```

Good:

```python
# Single, clear assignment
x = 10

# Only reassign when the value changes
y = "hello"
# ... some code ...
y = "updated value"  # Value actually changes
```
