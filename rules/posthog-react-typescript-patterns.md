---
include: "*.tsx,*.ts"
title: posthog React Typescript Patterns
tags: typescript,react
repo: PostHog/posthog
---

Use Kea logic for all state management instead of React state hooks. Follow PostHog's two-layer architecture pattern.

State Management
Define state logic with Kea and connect to React components using `useValues` and `useActions`.

Component Structure
Use functional components with explicit return types and named exports.

Import/Export Conventions
Prefer named exports over default exports and use path aliases for clean imports.

TypeScript Requirements
Include explicit return types for all functions and use auto-generated types from Kea logic.

Bad:

```typescript
// Using React state hooks
import React, { useState, useEffect } from 'react'

export default function ExampleComponent() {
    const [data, setData] = useState(null)
    const [loading, setLoading] = useState(false)
    const [filter, setFilter] = useState('')

    useEffect(() => {
        setLoading(true)
        api.getData().then(setData).finally(() => setLoading(false))
    }, [])

    return <div>{/* Component JSX */}</div>
}
```

Good:

```typescript
// Using Kea for state management
export const exampleLogic = kea<exampleLogicType>([
    path(['scenes', 'example']),
    actions({
        loadData: true,
        setFilter: (filter: string) => ({ filter }),
    }),
    reducers({
        filter: ['', { setFilter: (_, { filter }) => filter }],
    }),
    loaders(() => ({
        data: {
            loadData: async () => {
                return await api.getData()
            },
        },
    })),
])

export function ExampleComponent(): JSX.Element {
    const { data, loading, filter } = useValues(exampleLogic)
    const { loadData, setFilter } = useActions(exampleLogic)

    return (
        <div>
            {/* Component JSX */}
        </div>
    )
}
```
