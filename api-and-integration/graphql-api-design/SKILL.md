---
name: graphql-api-design
description: "Design GraphQL APIs from specifications, schemas, or natural language descriptions."
license: "MIT"
---

## Workflow

This skill is designed to facilitate the creation of GraphQL APIs. The process begins with the user providing a specification, which can be in the form of a natural language description, a database schema, or an existing API definition. The agent then analyzes this input to understand the data entities, their relationships, and the desired operations (queries, mutations, and subscriptions).

Based on this analysis, the agent generates a GraphQL schema in Schema Definition Language (SDL). This schema defines the types, fields, and operations of the API. The agent also creates resolver templates for the defined operations, which can be filled in with the business logic for data fetching and manipulation.

Finally, the agent can optionally generate a complete GraphQL server project with the schema and resolvers integrated, using a framework like Apollo Server or a similar library.

## Usage

To use this skill, you should provide a clear and detailed description of the desired API. This can include:

*   **Data models:** The entities in your system and their attributes.
*   **Relationships:** How the entities are connected to each other (e.g., one-to-one, one-to-many).
*   **Operations:** The specific queries, mutations, and subscriptions you want to expose.

The agent will then use this information to generate the GraphQL API. You can iterate on the design by providing feedback and requesting changes to the generated schema and resolvers.

## Example

**User Request:**

> I need a GraphQL API for a simple blog. It should have `User` and `Post` types. Users can have multiple posts, and each post has an author. I want to be able to fetch all posts, fetch a single post by its ID, and create a new post.

**Generated `schema.graphql`:**

```graphql
type User {
  id: ID!
  name: String!
  email: String!
  posts: [Post!]!
}

type Post {
  id: ID!
  title: String!
  content: String!
  author: User!
}

type Query {
  posts: [Post!]!
  post(id: ID!): Post
}

type Mutation {
  createPost(title: String!, content: String!, authorId: ID!): Post
}
```

This example demonstrates how the agent can take a high-level description and produce a concrete GraphQL schema that serves as the foundation for the API. The next step would be to implement the resolvers for the `posts`, `post`, and `createPost` operations.
