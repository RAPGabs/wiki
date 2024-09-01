---
id: apollo
title: Apollo (GraphQL)
---

Apollo is a comprehensive state management library for JavaScript that enables you to manage both local and remote data with GraphQL. Use it to fetch, cache, and modify application data, all while automatically updating your UI.

## GraphQL

GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables powerful developer tools.

**Describe Your Data:**
```bash
type Project {
  name: String
  tagline: String
  contributors: [User]
}
```

**Demand Whatever You Need:**
```bash
{
  project(name: "GraphQL") {
    tagline
  }
}
```

**Result**
```bash
{
  "project": {
    "tagline": "A query language for APIs"
  }
}
```
#### References
Please refer to the below references for more detail-

- **Apollo Documentation**-

[``https://www.apollographql.com/docs/apollo-server/``](https://www.apollographql.com/docs/apollo-server/)

## Resolvers
A resolver is a function that's responsible for populating the data for a single field in your schema. It can populate that data in any way you define, such as by fetching data from a back-end database or a third-party API.

**Note:**If you don't define a resolver for a particular field, Apollo Server automatically defines a default resolver for it.

**Syntax:**
```bash
/*
for a schema like this->
type Query {
  numberSix: Int! # Should always return the number 6 when queried
  numberSeven: Int! # Should always return 7
}
*/

//The resolver looks like:
const resolvers = {
  Query: {
    numberSix() {
      return 6;
    },
    numberSeven() {
      return 7;
    }
  }
};
```
#### References
Please refer to the below references for more detail-

- **Apollo Documentation**-

[``https://www.apollographql.com/docs/apollo-server/data/resolvers``](https://www.apollographql.com/docs/apollo-server/data/resolvers)

## Schema,Queries, And Mutation

### Schema Definition Language (SDL) / Schema
The GraphQL specification defines a human-readable schema definition language (or SDL) that you use to define your schema and store it as a string.

Here's a short example schema that defines two object types: Book and Author:
```bash
type Book {
  title: String
  author: Author
}

type Author {
  name: String
  books: [Book]
}
```
A schema defines a collection of types and the relationships between those types. In the example schema above, a Book can have an associated author, and an Author can have a list of books.

**Fields:** Most of the schema types you define have one or more fields.Each field returns data of the type specified. A field's return type can be a `scalar, object, enum, union, or interface (all described below)`.

### Queries
At its simplest, GraphQL is about asking for specific fields on objects.

**For Example:**
```bash
//Simple Query Operation
query Query {
  getAll {
    AccountId
    QuoteNumber
    PolicyNumber
  }
}

//Query Operation With Arguments
human(id: "1000") {
    name
    height
  }
}
```

### Mutation
Most discussions of GraphQL focus on data fetching, but any complete data platform needs a way to modify server-side data as well.

In REST, any request might end up causing some side-effects on the server, but by convention it's suggested that one doesn't use GET requests to modify data. GraphQL is similar - technically any query could be implemented to cause a data write. However, it's useful to establish a convention that any operations that cause writes should be sent explicitly via a mutation.

Just like in queries, if the mutation field returns an object type, you can ask for nested fields. This can be useful for fetching the new state of an object after an update. Let's look at a simple example mutation:
```bash
mutation CreateReviewForEpisode($ep: Episode!, $review: ReviewInput!) {
  createReview(episode: $ep, review: $review) {
    stars
    commentary
  }
}

{
  "ep": "JEDI",
  "review": {
    "stars": 5,
    "commentary": "This is a great movie!"
  }
}

{
  "data": {
    "createReview": {
      "stars": 5,
      "commentary": "This is a great movie!"
    }
  }
}
```
#### References
Please refer to the below references for more detail-

- **GraphQL Documentation**-

[``https://graphql.org/learn/queries/#gatsby-focus-wrapper``](https://graphql.org/learn/queries/#gatsby-focus-wrapper)

## Apollo Server

Apollo Server is an open-source, spec-compliant GraphQL server that's compatible with any GraphQL client, including Apollo Client. It's the best way to build a production-ready, self-documenting GraphQL API that can use data from any source.

You can use Apollo Server as:
- A gateway for a federated supergraph
    - The GraphQL server for a subgraph in a federated supergraph
- A stand-alone GraphQL server, including in a serverless environment
- An add-on to your application's existing Node.js middleware (such as Express or Fastify)

Apollo Server provides:
- Straightforward setup, so your client developers can start fetching data quickly
- Incremental adoption, allowing you to add features as they're needed
- Universal compatibility with any data source, any build tool, and any GraphQL client
- Production readiness, enabling you to ship features faster

**Example:**
```bash
const server = new ApolloServer({
    typeDefs,
    resolvers,
    plugins: [GraphQlPlugin],
    context : ( { request}) => ({
      
      userInfo : {
        userName: request.headers['sso-userName'],
        firstName: request.headers['sso-firstName'],
        lastName: request.headers['sso-lastName'],
        roles: request.headers['sso-roles'],
        features: request.headers['sso-features']
      }
    })
    });
```
#### References
Please refer to the below references for more detail-

- **Apollo Documentation**-

[``https://www.apollographql.com/docs/apollo-server/``](https://www.apollographql.com/docs/apollo-server/)

## Apollo Client

Apollo Client is a comprehensive state management library for JavaScript that enables you to manage both local and remote data with GraphQL. Use it to fetch, cache, and modify application data, all while automatically updating your UI.

Apollo Client helps you structure code in an economical, predictable, and declarative way that's consistent with modern development practices. The core `@apollo/client` library provides built-in integration with React, and the larger Apollo community maintains integrations for other popular view layers.

**Features**

- **Declarative data fetching**: Write a query and receive data without manually tracking loading states.
Excellent developer experience: Enjoy helpful tooling for TypeScript, Chrome / Firefox devtools, and VS Code.
- **Designed for modern React**: Take advantage of the latest React features, such as hooks.
- **Incrementally adoptable**: Drop Apollo into any JavaScript app and incorporate it feature by feature.
- **Universally compatible**: Use any build setup and any GraphQL API.
- **Community driven**: Share knowledge with thousands of developers in the GraphQL community.
#### References
Please refer to the below references for more detail-

- **Apollo Documentation**-

[``https://www.apollographql.com/docs/react``](https://www.apollographql.com/docs/react)

## GraphQL Plugins

You can create your own Apollo Server plugins to perform custom operations in response to certain events. For example, a basic logging plugin might log the GraphQL query string associated with each request that's sent to Apollo Server.

Plugins are JavaScript objects that implement one or more functions that respond to events. Here's a basic plugin that responds to the serverWillStart event:
```bash
const myPlugin = {
  async serverWillStart() {
    console.log('Server starting up!');
  },
```

A plugin specifies exactly which events it responds to by implementing functions that correspond to those events. The plugin in the examples above responds to the serverWillStart event, which fires when Apollo Server is preparing to start up. Almost all plugin events are async functions (i.e., functions that return Promises). The only exceptions are willResolveField and schemaDidLoadOrUpdate.

Plugins can respond to the following events associated with the GraphQL request lifecycle:

- `didResolveSource`
- `parsingDidStart`
- `validationDidStart`
- `didResolveOperation`
- `responseForOperation`
- `executionDidStart`
- `didEncounterErrors`
- `willSendResponse`

**Example**
```bash
async validationDidStart(requestContext) {
        if (requestContext.request.operationName == "Mutation") {
          console.log(schema);
          const validatorResult = await verifyJSON(
            ajv, schema, requestContext.request.variables.input
          );
```
**Note:** One important use case of a plugin is that it can be used as a hook for a http request to Apollo Server.Thus any changes,validations,etc can be performed on the input request before sending the request to the Apollo Server.
#### References
Please refer to the below references for more detail-

- **Apollo Documentation**-

[``https://www.apollographql.com/docs/apollo-server/integrations/plugins/``](https://www.apollographql.com/docs/apollo-server/integrations/plugins/)





