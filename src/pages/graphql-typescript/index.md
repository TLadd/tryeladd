---
title: Using Typescript for GraphQL Resolvers
date: '2018-12-02T22:12:03.284Z'
---

GraphQL and Typescript are both great. They can be great together, and it's really easy!

## Why use Typescript for GraphQL Resolvers?

GraphQL's schema language already comes with a type system. The schema defintion is nothing more than a collection of types. If your resolver returns data that is not valid for the specified schema, you will receive an error similar to this:

// Insert error

So what does using Typescript buy us? Like with most applications, using Typescript provides the following advantages:

1.  Find inconsistencies quickly. While a good test suite can find a lot of the same errors (and can also find logic errors that Typescript cannot), finding bugs as quickly as possible helps save time.
2.  Improved developer experience with VSCode and other IDE Typescript integrations. Autocomplete, Go-to-definition etc.

Additionally, Typescript is particularly well-suited for GraphQL resolvers becuse

- The GraphQL schema provides a wealth of type information already. This makes it easy to generate Typescript types, which reduces the amount of work the developer has to do manually.
- GraphQL resolvers generally follow a structure of retrieving data from somewhere (another API or a datastore), optionally doing some sort of transformation or normalization on that data, and then returning it. Type coverage on the resolvers ensures we don't muck anything up between retrieving the data and returning it, which is really all there is to a resolver.

## Sample Schema

We're going to use this schema as an example to demonstrate all you need to do to get full type coverage on GraphQL resolvers.

```graphql
type Query {
  account(id: ID!): Account
}

type Account {
  id: ID!
  name: String!
  posts: [Post!]
}

type Post {
  id: ID!
  content: String!
  comments: [Comment!]
}

type Comment {
  id: ID!
  content: String!
}
```

## Generating Types for Schema

## Using Types in Resolvers

## Specifying Custom Context Type

## Using Mappers
