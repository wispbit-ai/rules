---
include: "*.py"
title: Consistent error classes in Python
tags: python
---

Use consistent naming conventions for error classes in Python.

Bad:

```python
class PublicAPiError(Exception):
    # Inconsistent casing in "APi" - should be either "Api" or "API"
    pass

class UnauthorizedHTtpError(Exception):
    # Inconsistent casing in "HTtp" - should be either "Http" or "HTTP"
    pass
```

Good:

```python
class PublicApiError(Exception):
    # Consistent Pascal casing with "Api"
    pass

class UnauthorizedHttpError(Exception):
    # Consistent Pascal casing with "Http"
    pass
```
