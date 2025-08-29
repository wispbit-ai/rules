---
include: "*.ts,*.mts,*.cts,*.js,*.cjs,*.mjs"
title: Prefer with syntax in Typescript
tags: typescript,javascript
---

Use the newer `with` syntax for JSON imports instead of the deprecated `assert` syntax for Node.js compatibility.

Bad:

```javascript
import data from "./data.json" assert { type: "json" }
```

Good:

```javascript
import data from "./data.json" with { type: "json" }
```
