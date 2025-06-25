# 📦 MongoDB

## Introduction

MongoDB est une base de données NoSQL orientée documents. Elle est conçue pour stocker des données non structurées ou semi-structurées, offrant une flexibilité et une scalabilité élevées. Contrairement aux bases de données relationnelles, MongoDB utilise des collections et des documents au format BSON (Binary JSON) pour organiser les données.

---

## Concepts clés

### Pourquoi utiliser MongoDB ?

1. **Flexibilité des schémas** : MongoDB permet de stocker des données sans schéma fixe, ce qui est idéal pour les applications évolutives.
2. **Scalabilité horizontale** : MongoDB prend en charge le sharding pour répartir les données sur plusieurs serveurs.
3. **Performances élevées** : Les index et les opérations en mémoire garantissent des performances optimales.
4. **Support des données complexes** : MongoDB peut gérer des structures imbriquées et des types de données avancés comme les tableaux et les objets.

### Enjeux pour les développeurs

1. **Validation des données** : Implémentez des mécanismes de validation pour garantir l'intégrité des données.
2. **Gestion des performances** : Configurez les index et surveillez les requêtes pour éviter les ralentissements.
3. **Sécurisation des données** : Protégez les données sensibles avec des mécanismes comme le chiffrement et l'authentification.
4. **Sauvegarde et restauration** : Automatisez les sauvegardes pour garantir la récupération des données en cas de panne.

---

## Commandes essentielles

### Gestion des bases de données

```bash
mongo                              # Connecte au shell MongoDB
show dbs                           # Liste les bases de données
use <database>                     # Change de base de données
db.createCollection('users')       # Crée une collection
db.dropDatabase()                  # Supprime une base de données
```

### Gestion des collections

```bash
db.users.find()                    # Liste tous les documents d'une collection
db.users.countDocuments()          # Compte le nombre de documents dans une collection
db.users.renameCollection('newName') # Renomme une collection
db.users.drop()                    # Supprime une collection
```

### Gestion des documents

```bash
db.users.insert({ name: 'Alice', age: 25 })  # Insère un document
db.users.find({ name: 'Alice' })            # Recherche des documents
db.users.update({ name: 'Alice' }, { $set: { age: 26 } }) # Met à jour un document
db.users.deleteOne({ name: 'Alice' })       # Supprime un document
db.users.aggregate([{ $group: { _id: "$age", count: { $sum: 1 } } }]) # Utilise l'agrégation
```

### Gestion des index

```bash
db.users.createIndex({ name: 1 })           # Crée un index sur le champ "name"
db.users.getIndexes()                       # Liste les index existants
db.users.dropIndex("name_1")                # Supprime un index
```

### Sauvegarde et restauration

```bash
mongodump --db=<database> --out=<path>      # Sauvegarde une base de données
mongorestore --db=<database> <path>        # Restaure une base de données
```

---

## Exemples pratiques

### Exemple de document MongoDB

```json
{
  "_id": "12345",
  "name": "Alice",
  "email": "alice@example.com",
  "age": 25,
  "address": {
    "street": "123 Main St",
    "city": "Wonderland"
  },
  "tags": ["admin", "user"]
}
```

### Exemple de requête avec agrégation

```javascript
db.users.aggregate([
  { $match: { age: { $gte: 18 } } },
  { $group: { _id: "$age", count: { $sum: 1 } } },
  { $sort: { count: -1 } }
]);
```

### Exemple avec Mongoose (Node.js)

```javascript
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  name: String,
  email: { type: String, unique: true },
  age: Number,
  isActive: { type: Boolean, default: true },
});

const User = mongoose.model('User', userSchema);

async function createUser() {
  const user = new User({ name: 'Alice', email: 'alice@example.com', age: 25 });
  await user.save();
  console.log('User created:', user);
}
```

---

## Bonnes pratiques

1. **Indexation** : Ajoutez des index pour accélérer les requêtes, surtout sur les champs fréquemment utilisés.
2. **Validation des schémas** : Utilisez des outils comme Mongoose ou les validations JSON Schema pour garantir l'intégrité des données.
3. **Sauvegarde régulière** : Automatisez les sauvegardes avec `mongodump` pour éviter les pertes de données.
4. **Surveiller les performances** : Utilisez `explain()` pour analyser les requêtes et optimiser les index.
5. **Sécuriser les connexions** : Configurez SSL/TLS et utilisez l'authentification pour protéger les données sensibles.
6. **Partitionnement des données** : Utilisez le sharding pour répartir les données sur plusieurs serveurs et améliorer la scalabilité.

---

## Outils utiles

- **MongoDB Compass** : Interface graphique pour gérer MongoDB.
- **Mongoose** : ODM (Object Document Mapper) pour Node.js.
- **Robo 3T** : Client léger pour MongoDB.
- **Studio 3T** : Outil avancé pour MongoDB avec support des requêtes visuelles.
- **mongodump/mongorestore** : Outils en ligne de commande pour sauvegarder et restaurer les bases de données.

---

## Liens utiles

- [Documentation MongoDB](https://www.mongodb.com/docs/)
- [Mongoose](https://mongoosejs.com/)
- [MongoDB Compass](https://www.mongodb.com/products/compass)
- [Studio 3T](https://studio3t.com/)
- [Tutoriels MongoDB](https://www.tutorialspoint.com/mongodb/index.htm)
