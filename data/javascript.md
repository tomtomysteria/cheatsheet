# 📦 JavaScript / TypeScript

## Introduction

JavaScript est un langage de programmation utilisé pour le développement web côté client et côté serveur. TypeScript est un sur-ensemble de JavaScript qui ajoute des types statiques pour améliorer la robustesse et la maintenabilité du code. Ces deux langages sont essentiels pour créer des applications modernes, interactives et performantes.

---

## NPM - Gestionnaire de paquets pour JavaScript

NPM est utilisé pour installer, gérer et exécuter des dépendances dans les projets JavaScript.

### Commandes essentielles

```bash
npm init -y          # Initialise un projet avec les paramètres par défaut
npm install <package> # Installe un package
npm uninstall <package> # Désinstalle un package
npm run <script>     # Exécute un script défini dans package.json
npm update           # Met à jour les dépendances
npm list             # Liste les dépendances installées
npm audit            # Analyse les vulnérabilités des dépendances
npm cache clean --force # Nettoie le cache NPM
npm outdated         # Liste les packages obsolètes
```

### Exemples pratiques

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "scripts": {
    "start": "node index.js",
    "test": "jest",
    "build": "webpack --mode production"
  }
}
```

---

## Yarn - Alternative à NPM

Yarn est un gestionnaire de paquets rapide et fiable pour JavaScript.

### Commandes essentielles

```bash
yarn init            # Initialise un projet
yarn add <package>   # Ajoute un package
yarn remove <package> # Supprime un package
yarn run <script>    # Exécute un script défini dans package.json
yarn upgrade         # Met à jour les dépendances
yarn cache clean     # Nettoie le cache Yarn
yarn outdated        # Liste les packages obsolètes
```

### Exemples pratiques

```bash
yarn add react react-dom
yarn run start
```

---

## Modules JavaScript

Les modules permettent de structurer le code en fichiers réutilisables.

### Exemple de module

#### Fichier `math.js`

```javascript
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

#### Fichier `app.js`

```javascript
import { add, subtract } from './math.js';

console.log(add(5, 3)); // 8
console.log(subtract(5, 3)); // 2
```

---

## Gestion des erreurs

### Exemple de gestion des erreurs

```javascript
try {
  const result = JSON.parse('{"key": "value"}');
  console.log(result.key);
} catch (error) {
  console.error('Erreur lors du parsing JSON :', error.message);
} finally {
  console.log('Opération terminée.');
}
```

---

## Développement backend avec JavaScript

### Exemple de contrôleur avec Express.js

```javascript
import express from 'express';

const app = express();

app.get('/api/hello', (req, res) => {
  res.send('Hello, JavaScript Backend!');
});

app.listen(3000, () => {
  console.log('Serveur démarré sur le port 3000');
});
```

### Exemple de modèle (DTO)

```javascript
export class UserDTO {
  constructor(id, name, email) {
    this.id = id;
    this.name = name;
    this.email = email;
  }
}
```

### Exemple de service

```javascript
export class UserService {
  getUserById(id) {
    return new UserDTO(id, 'Alice', 'alice@example.com');
  }
}
```

---

## Tests avec JavaScript

### Utilisation de Jest

Ajoutez Jest au projet :

```bash
npm install --save-dev jest
```

Exemple de test :

```javascript
// filepath: math.test.js
import { add } from './math.js';

test('addition de 2 et 3 donne 5', () => {
  expect(add(2, 3)).toBe(5);
});
```

Exécutez les tests :

```bash
npm test
```

---

## TypeScript - Superset de JavaScript

TypeScript ajoute des types statiques à JavaScript, ce qui améliore la robustesse du code.

### Commandes essentielles

```bash
tsc --init           # Initialise un projet TypeScript
tsc index.ts         # Compile un fichier TypeScript
tsc --watch          # Compile en mode veille
```

### Exemple de code TypeScript

```typescript
function greet(name: string): string {
  return `Hello, ${name}!`;
}

console.log(greet("World"));
```

---

## Gestion des logs

### Exemple de logs avec `console`

```javascript
console.log('Info : opération réussie');
console.warn('Avertissement : attention à cette étape');
console.error('Erreur : une exception est survenue');
```

### Utilisation de Winston pour des logs avancés

Ajoutez Winston au projet :

```bash
npm install winston
```

Exemple de configuration :

```javascript
import winston from 'winston';

const logger = winston.createLogger({
  level: 'info',
  format: winston.format.json(),
  transports: [
    new winston.transports.Console(),
    new winston.transports.File({ filename: 'logs/app.log' }),
  ],
});

logger.info('Application démarrée');
logger.error('Une erreur est survenue');
```

---

## Bonnes pratiques

1. **Utiliser des modules** : Structurez le code en modules pour améliorer la maintenabilité.
2. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
3. **Utiliser TypeScript** : Ajoutez des types statiques pour réduire les erreurs.
4. **Analyser les vulnérabilités** : Utilisez `npm audit` ou `yarn audit` pour détecter les failles de sécurité.
5. **Activer les logs** : Configurez des logs pour surveiller les performances et les erreurs.
6. **Minimiser le code** : Utilisez des outils comme Webpack ou Rollup pour optimiser les fichiers JavaScript.
7. **Structurer les projets** : Organisez les projets en couches (ex. contrôleurs, services, modèles) pour améliorer la maintenabilité.

---

## Liens utiles

- [Documentation JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [Documentation TypeScript](https://www.typescriptlang.org/docs/)
- [Documentation NPM](https://docs.npmjs.com/)
- [Documentation Yarn](https://yarnpkg.com/)
- [Documentation Jest](https://jestjs.io/docs/getting-started)
- [Documentation Express.js](https://expressjs.com/)
