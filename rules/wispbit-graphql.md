---
include: "*.graphql"
title: wispbit GraphQL standards
tags: graphql
repo: wispbit/cloud
---

Follow these patterns for GraphQL mutations to ensure consistency and extensibility:

Input Parameters
Use a single `input` parameter instead of individual parameters for all mutations.

Naming Conventions

- Input types: `...Input` (e.g., `UpdateRepositoryInput`, `CreateUserInput`)
- Return types: `...Payload` (e.g., `UpdateRepositoryPayload`, `CreateUserPayload`)

Update Mutations
Use a single generic update method per entity that can be extended by adding fields to the input type.

Bad:

```graphql
updateRepositorySkippedBranches(
  repositoryId: ID!
  skippedBranches: [String!]!
): Repository!

updateRepositoryName(
  repositoryId: ID!
  name: String!
): Repository!
```

Good:

```graphql
updateRepository(input: UpdateRepositoryInput!): UpdateRepositoryPayload!

input UpdateRepositoryInput {
  repositoryId: ID!
  skippedBranches: [String!]
  name: String
}

type UpdateRepositoryPayload {
  repository: Repository!
}
```
