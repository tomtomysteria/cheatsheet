# 📦 Node.js

## Introduction

Node.js est un environnement d'exécution JavaScript côté serveur basé sur le moteur V8 de Google. Il permet de créer des applications web, des API REST, des microservices, et des outils CLI. Grâce à son architecture non bloquante et événementielle, Node.js est idéal pour les applications nécessitant une haute performance et une scalabilité. Il est souvent utilisé avec Express.js pour simplifier le développement d'applications backend.

---

## Commandes essentielles

### Node.js CLI

```bash
node <file>.js                        # Exécute un fichier JavaScript
npm init -y                           # Initialise un projet avec les paramètres par défaut
npm install <package>                 # Installe un package
npm uninstall <package>               # Supprime un package
npm update                            # Met à jour les dépendances
npm run <script>                      # Exécute un script défini dans package.json
npm test                              # Exécute les tests
npm audit                             # Analyse les vulnérabilités des dépendances
npm cache clean --force               # Nettoie le cache NPM
npm list                              # Liste les dépendances installées
npm outdated                          # Liste les packages obsolètes
```

---

## Concepts clés

### Exemple de serveur HTTP

```javascript
// filepath: server.js
const http = require('http');

const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello, Node.js!');
});

server.listen(3000, () => {
    console.log('Serveur démarré sur le port 3000');
});
```

---

## Développement d'API REST avec Express.js

### Exemple de contrôleur

```javascript
// filepath: controllers/helloController.js
exports.sayHello = (req, res) => {
    res.json({ message: 'Hello, API!' });
};
```

### Exemple de route

```javascript
// filepath: routes/helloRoutes.js
const express = require('express');
const router = express.Router();
const helloController = require('../controllers/helloController');

router.get('/hello', helloController.sayHello);

module.exports = router;
```

### Exemple de serveur Express

```javascript
// filepath: server.js
const express = require('express');
const helloRoutes = require('./routes/helloRoutes');

const app = express();
app.use(express.json());
app.use('/api', helloRoutes);

app.listen(3000, () => {
    console.log('Serveur démarré sur le port 3000');
});
```

---

## Modèles et DTOs

### Exemple de modèle

```javascript
// filepath: models/User.js
class User {
    constructor(id, name, email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }
}

module.exports = User;
```

### Exemple de DTO

```javascript
// filepath: dtos/UserDTO.js
class UserDTO {
    constructor(id, name, email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }
}

module.exports = UserDTO;
```

---

## ORM avec Sequelize

### Exemple d'entité Sequelize

```javascript
// filepath: entities/User.js
const { DataTypes } = require('sequelize');
const sequelize = require('../config/database');

const User = sequelize.define('User', {
    id: {
        type: DataTypes.INTEGER,
        autoIncrement: true,
        primaryKey: true,
    },
    name: {
        type: DataTypes.STRING,
        allowNull: false,
    },
    email: {
        type: DataTypes.STRING,
        allowNull: false,
        unique: true,
    },
});

module.exports = User;
```

### Configuration de Sequelize

```javascript
// filepath: config/database.js
const { Sequelize } = require('sequelize');

const sequelize = new Sequelize('database', 'username', 'password', {
    host: 'localhost',
    dialect: 'mysql',
});

module.exports = sequelize;
```

---

## Services

### Exemple de service

```javascript
// filepath: services/userService.js
const UserDTO = require('../dtos/UserDTO');
const User = require('../entities/User');

exports.getUserById = async (id) => {
    const user = await User.findByPk(id);
    if (!user) {
        throw new Error('Utilisateur non trouvé');
    }
    return new UserDTO(user.id, user.name, user.email);
};
```

---

## Tests avec Node.js

### Utilisation de Jest

Ajoutez Jest au projet :

```bash
npm install --save-dev jest
```

#### Exemple de test

```javascript
// filepath: __tests__/userService.test.js
const userService = require('../services/userService');

test('retourne un utilisateur par ID', async () => {
    const user = await userService.getUserById(1);
    expect(user).toEqual({ id: 1, name: 'Alice', email: 'alice@example.com' });
});
```

Exécutez les tests :

```bash
npm test
```

---

## Gestion des logs

### Utilisation de `console`

```javascript
// filepath: utils/logger.js
exports.logInfo = (message) => console.log(`Info : ${message}`);
exports.logWarn = (message) => console.warn(`Avertissement : ${message}`);
exports.logError = (message) => console.error(`Erreur : ${message}`);
```

---

## Bonnes pratiques

1. **Structurer les projets** : Organisez les fichiers en dossiers (ex. `controllers`, `routes`, `models`, `services`, `dtos`, `entities`) pour améliorer la maintenabilité.
2. **Utiliser les middlewares** : Implémentez des middlewares pour gérer les erreurs, la validation, et l'authentification.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
4. **Activer les logs** : Utilisez `console` ou des bibliothèques comme `winston` pour surveiller les performances et les erreurs.
5. **Sécuriser les endpoints** : Utilisez des bibliothèques comme `jsonwebtoken` pour gérer l'authentification et l'autorisation.
6. **Configurer les environnements** : Utilisez des fichiers `.env` pour gérer les variables d'environnement.
7. **Utiliser Sequelize** : Simplifiez la gestion des bases de données avec Sequelize.

---

## Liens utiles

- [Documentation officielle Node.js](https://nodejs.org/en/docs/)
- [Documentation Express.js](https://expressjs.com/)
- [Documentation Sequelize](https://sequelize.org/)
- [Tutoriels Node.js](https://www.w3schools.com/nodejs/)
- [Exemples de projets Node.js](https://github.com/nodejs/examples)
