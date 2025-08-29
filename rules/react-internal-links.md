---
include: "*.tsx"
title: Internal links in React
tags: react,typescript
---

When linking between internal sites, use `rel="noopener"` instead of `rel="noopener noreferrer"`.

Bad:

```jsx
// For internal links, don't use noreferrer
<Link to="/dashboard" rel="noopener noreferrer">Dashboard</Link>

// Or with anchor tags
<a href="/about" rel="noopener noreferrer">About Us</a>
```

Good:

```jsx
// For internal links, only use noopener
<Link to="/dashboard" rel="noopener">Dashboard</Link>

// Or with anchor tags
<a href="/about" rel="noopener">About Us</a>

// For external links, noreferrer can be appropriate
<a href="https://external-site.com" rel="noopener noreferrer" target="_blank">External Site</a>
```
