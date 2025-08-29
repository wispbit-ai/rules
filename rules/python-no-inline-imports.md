---
include: "*.py"
title: No inline imports in Python
tags: python
---

Place all import statements at the top of the file.

Bad:

```python
def process_data(data: Dict) -> List:
    import os  # Inline import
    import json  # Inline import
    from mymodule import MyClass  # Inline import

    file_path = os.path.join("data", "output.json")
    with open(file_path, "w") as f:
        json.dump(data, f)

    processor = MyClass()
    return processor.transform(data)
```

Good:

```python
import os
import json
from typing import Dict, List
from mymodule import MyClass

def process_data(data: Dict) -> List:
    # Use imported modules here
    file_path = os.path.join("data", "output.json")
    with open(file_path, "w") as f:
        json.dump(data, f)

    processor = MyClass()
    return processor.transform(data)
```
