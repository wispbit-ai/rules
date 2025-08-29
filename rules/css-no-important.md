---
include: "*.css"
title: No important tag in CSS
tags: css
---

Do not use the `!important` declaration in CSS styles.

Bad:

```css
.element {
  color: red !important;
  margin-top: 10px !important;
}
```
