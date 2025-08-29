---
include: "*.py"
title: Early returns in Python
tags: python
---

Use early returns to reduce nesting levels. Instead of wrapping large code blocks in conditional statements, return early when conditions are not met.

Bad:

```python
def process_user(user):
    if user is not None:
        if user.is_active:
            # Many lines of processing code
            result = perform_complex_operation(user)
            return result
    return None
```

Good:

```python
def process_user(user):
    if user is None:
        return None

    if not user.is_active:
        return None

    # Now we can work with user without nesting
    # Many lines of processing code
    result = perform_complex_operation(user)
    return result
```
