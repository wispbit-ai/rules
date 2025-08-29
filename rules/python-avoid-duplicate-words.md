---
include: "*.py"
title: Avoid duplicate words in Python
tags: python
---

Check all text elements (comments, docstrings, and string literals) for duplicate adjacent words for typos or duplicates.

Bad:

```python
# This function validates the the input parameters
def validate_input(data):
    ...
```

Good:

```python
# This function validates the input parameters
def validate_input(data):
    ...
```
