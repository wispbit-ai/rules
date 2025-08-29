---
include: "*.rs"
title: Check character boundaries in Rust
tags: rust
---

When truncating strings, ensure you check character boundaries to prevent panics with multi-byte UTF-8 characters.

Bad:

```rust
// This can cause a panic if truncation happens in the middle of a multi-byte character
let mut value = some_string;
value.truncate(limit);
```

Good:

```rust
// Check character boundaries before truncating
let mut value = some_string;
let mut index = limit;
while !value.is_char_boundary(index) {
    index -= 1;
}
value.truncate(index);
```
