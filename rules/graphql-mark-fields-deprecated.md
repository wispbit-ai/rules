---
include: "*.graphql"
title: Mark fields as deprecated in GraphQL
tags: graphql
---

When removing fields from a GraphQL schema, follow a progressive deprecation process:

1. First, mark the field to be removed as deprecated using the `@deprecated` directive
2. Introduce the new alternative field in the same operation
3. Only remove deprecated fields after they have been deprecated for a sufficient time period

Bad:

```graphql
// Before
type User {
  id: ID!
  oldEmail: String!
}

// After (directly removing the field)
type User {
  id: ID!
}
```

Good:

```graphql
// Step 1: Mark as deprecated and introduce alternative
type User {
  id: ID!
  oldEmail: String! @deprecated(reason: "Use 'email' field instead")
  email: String!
}

// Step 2: Only later, remove the deprecated field
type User {
  id: ID!
  email: String!
}
```
