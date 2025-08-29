---
include: "*.rs"
title: Use triple slash for documentation in Rust
tags: rust
---

Use triple slashes (`///`) for documenting Rust functions and methods.
Bad:

```rust
// This function processes tenant requests
fn process_tenant_request() {
    // implementation
}
```

Good:

```rust
/// This function processes tenant requests
fn process_tenant_request() {
    // implementation
}
```
