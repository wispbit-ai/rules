---
include: "package.json"
title: Dev dependencies in typescript
tags: typescript,react,nextjs
---

Place CLI tool dependencies in the `devDependencies` section of `package.json` instead of `dependencies` when they are only used for local development, scripts, or tooling.

Bad:

```json
{
  "dependencies": {
    "@eslint/eslintrc": "^3",
    "@tailwindcss/postcss": "^4.1.6",
    "@types/node": "^20"
  }
}
```

Good:

```json
{
  "devDependencies": {
    "@eslint/eslintrc": "^3",
    "@tailwindcss/postcss": "^4.1.6",
    "@types/node": "^20"
  }
}
```
