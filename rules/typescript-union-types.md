---
include: "*.ts,*.tsx"
title: Use union types in Typescript
tags: typescript
---

Use union types with specific interfaces for mutually exclusive properties instead of a single interface with multiple optional properties.

Bad:

```typescript
interface ConfigOptions {
  fileConfig?: {
    path: string
    encoding?: string
  }
  dbConfig?: {
    connectionString: string
    poolSize?: number
  }
  properties?: Record<string, any>
}
```

Good:

```typescript
interface FileConfigOptions {
  fileConfig: {
    path: string
    encoding?: string
  }
  properties?: Record<string, any>
}

interface DbConfigOptions {
  dbConfig: {
    connectionString: string
    poolSize?: number
  }
  properties?: Record<string, any>
}

type ConfigOptions = FileConfigOptions | DbConfigOptions
```
