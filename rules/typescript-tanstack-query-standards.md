---
include: "*.ts,*.tsx"
title: Query standards for Tanstack Query
tags: typescript,react,nextjs
---

When using TanStack Query (React Query), always configure cache and refetching behavior explicitly:

1. Set appropriate `staleTime` based on how frequently the data changes
2. Configure all refetching flags explicitly to prevent unnecessary network requests

Bad:

```tsx
const { data } = useQuery({
  queryKey: ["resource", id],
  queryFn: () => fetchResource(id),
  refetchOnMount: false,
  // Missing staleTime and other refetching settings
})
```

Good:

```tsx
const { data } = useQuery({
  queryKey: ["resource", id],
  queryFn: () => fetchResource(id),
  refetchOnMount: false,
  refetchOnWindowFocus: false,
  refetchOnReconnect: false,
  staleTime: 5 * 60 * 1000, // 5 minutes
})
```
