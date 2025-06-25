# 📦 GraphQL

## Introduction

GraphQL est un langage de requête pour les API qui permet de récupérer uniquement les données nécessaires. Il offre une alternative flexible et efficace aux API REST en permettant aux clients de spécifier exactement les données qu'ils souhaitent. GraphQL est particulièrement adapté aux applications modernes où les besoins en données varient selon les clients (web, mobile, etc.).

---

## Concepts clés

### Requêtes et mutations

- **Requêtes** : Permettent de récupérer des données depuis le serveur.
- **Mutations** : Permettent de modifier ou créer des données sur le serveur.

### Schéma

Le schéma définit la structure des données disponibles via l'API GraphQL. Il inclut les types, les requêtes, et les mutations.

### Résolveurs

Les résolveurs sont des fonctions qui fournissent les données demandées par les clients. Chaque champ du schéma a un résolveur associé.

---

## Commandes essentielles

### Installation

```bash
npm install graphql
npm install express express-graphql
```

### Démarrer un serveur GraphQL

```javascript
// filepath: server.js
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
4. **Valider les entrées** : Ajoutez des validations pour les arguments des mutations.
5. **Optimiser les performances** : Cachez les résultats des résolveurs pour réduire les temps de réponse.
6. **Surveiller les erreurs** : Implémentez une gestion des erreurs robuste pour les résolveurs.

---

## Enjeux du développement avec GraphQL

1. **Flexibilité** : Les clients peuvent demander uniquement les données nécessaires, réduisant la surcharge réseau.
2. **Évolutivité** : Les schémas GraphQL permettent d'ajouter facilement de nouveaux champs sans casser les clients existants.
3. **Complexité** : Les résolveurs peuvent devenir complexes pour des schémas très imbriqués.
4. **Sécurité** : Implémentez des limites de profondeur et de complexité pour éviter les abus des clients.
5. **Interopérabilité** : GraphQL fonctionne avec de nombreux langages et frameworks, facilitant son adoption.

---

## Commandes utiles pour GraphQL

### Installation et configuration

```bash
npm install graphql
npm install express express-graphql
```

### Démarrage du serveur

```bash
node server.js
```

### Test des requêtes

Utilisez GraphiQL ou des outils comme Postman pour tester vos requêtes et mutations.

---

## Liens utiles

- [Documentation officielle GraphQL](https://graphql.org/)
- [Tutoriels GraphQL](https://www.howtographql.com/)
- [Exemples de code GraphQL](https://github.com/graphql/graphql-js)
- [GraphQL Playground](https://github.com/graphql/graphql-playground)
