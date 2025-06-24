# 📦 GraphQL

## Introduction

GraphQL est un langage de requête pour les API qui permet de récupérer uniquement les données nécessaires. Il offre une alternative flexible et efficace aux API REST en permettant aux clients de spécifier exactement les données qu'ils souhaitent.

---

## Commandes essentielles

### Installation

```bash
npm install graphql
npm install express express-graphql
```

### Démarrer un serveur GraphQL

```javascript
const express = require('express');
const { graphqlHTTP } = require('express-graphql');
const { buildSchema } = require('graphql');

const schema = buildSchema(`
  type Query {
    hello: String
  }
`);

const root = {
  hello: () => 'Hello, GraphQL!',
};

const app = express();
app.use('/graphql', graphqlHTTP({
  schema: schema,
  rootValue: root,
  graphiql: true,
}));

app.listen(4000, () => console.log('Server running at http://localhost:4000/graphql'));
```

---

## Exemples pratiques

### Exemple de requête GraphQL

```graphql
query {
  user(id: "1") {
    name
    email
    posts {
      title
      content
    }
  }
}
```

### Exemple de mutation GraphQL

```graphql
mutation {
  createUser(name: "Alice", email: "alice@example.com") {
    id
    name
    email
  }
}
```

### Définition d'un schéma GraphQL

```graphql
type User {
  id: ID!
  name: String!
  email: String!
  posts: [Post]
}

type Post {
  id: ID!
  title: String!
  content: String!
}

type Query {
  user(id: ID!): User
}

type Mutation {
  createUser(name: String!, email: String!): User
}
```

---

## Bonnes pratiques

1. **Utiliser GraphiQL** : Activez GraphiQL pour tester facilement vos requêtes et mutations.
2. **Modulariser le schéma** : Divisez les schémas complexes en fichiers pour une meilleure maintenabilité.
3. **Limiter les requêtes profondes** : Implémentez des limites de profondeur pour éviter les abus des clients.

---

## Liens utiles

- [Documentation officielle GraphQL](https://graphql.org/)
- [Tutoriels GraphQL](https://www.howtographql.com/)
- [Exemples de code GraphQL](https://github.com/graphql/graphql-js)
