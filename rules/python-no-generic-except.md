---
include: "*.py"
title: No generic except in Python
tags: python
---

Avoid using generic `except:` or `except Exception:` statements.

Bad:

```python
def read_config_file(filepath):
    try:
        with open(filepath, 'r') as f:
            return json.load(f)
    except Exception:
        logger.error("Something went wrong")
        return {}
```

```python
def read_config_file(filepath):
    try:
        with open(filepath, 'r') as f:
            return json.load(f)
    except:
        return {}
```
