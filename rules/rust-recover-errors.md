---
include: "*.rs"
title: Prefer logging instead of panicking in Rust
tags: rust
---

Use logging instead of panicking for recoverable errors. For operations that might fail but don't compromise the entire application state, log the error and provide a fallback rather than panicking.

Bad:

```rust
let top = editor.row_for_block(decorations.prompt_block_id, cx).unwrap();
let bottom = editor.row_for_block(decorations.end_block_id, cx).unwrap();
```

Good:

```rust
let scroll_target_range = maybe!({
    let top = editor.row_for_block(decorations.prompt_block_id, cx)?.0 as f32;
    let bottom = editor.row_for_block(decorations.end_block_id, cx)?.0 as f32;
    Some((top, bottom))
});
if scroll_target_range.is_none() {
    log::error!("bug: failed to find blocks for scrolling to inline assist");
}

// Use a fallback value when the operation fails
let scroll_target_range = scroll_target_range.unwrap_or_else(|| {
    // fallback calculation
});
```
