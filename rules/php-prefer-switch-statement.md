---
include: "*.php"
title: Prefer switch statements in PHP
tags: php
---

Use switch statements when handling multiple attribute types.
Bad:

```php
foreach ($attributes as $attribute) {
    if ($attribute->getAttribute('type') === Database::VAR_RELATIONSHIP) {
        // Handle relationship attribute
    }

    if ($attribute->getAttribute('type') === Database::VAR_STRING) {
        // Handle string attribute
    }
}
```

Good:

```php
foreach ($attributes as $attribute) {
    $attributeType = $attribute->getAttribute('type');

    switch ($attributeType) {
        case Database::VAR_RELATIONSHIP:
            // Handle relationship attribute
            break;

        case Database::VAR_STRING:
            // Handle string attribute
            break;
    }
}
```
