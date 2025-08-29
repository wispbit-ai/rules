---
include: "**/*_test.py,**/test_*.py"
title: Avoid print in Python tests
tags: python
---

Avoid using `print()` statements in test files.

Bad:

```python
def test_example():
    result = some_function()
    print(result)  # Debugging statement left in the code
    assert result == expected_value
```

Good:

```python
def test_example():
    result = some_function()
    assert result == expected_value
```
