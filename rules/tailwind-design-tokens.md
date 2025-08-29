---
include: "*.tsx"
title: Prefer tailwind design tokens
tags: nextjs,tailwind
---

Use Tailwind's predefined design tokens instead of arbitrary values. Do not use custom pixel values, color codes, or arbitrary numbers in your Tailwind CSS classes.

1. Use Tailwind's spacing scale instead of arbitrary pixel values
2. Use Tailwind's color palette instead of custom color codes
3. Use Tailwind's z-index scale instead of arbitrary z-index values
4. Use Tailwind's percentage-based positioning values instead of arbitrary percentages

Bad:

```html
<div class="mt-[37px] text-[#3366FF] z-[9999] top-[37%] w-[142px]">
  Custom content
</div>
```

Good:

```html
<div class="mt-10 text-blue-600 z-50 top-1/3 w-36">Custom content</div>
```
