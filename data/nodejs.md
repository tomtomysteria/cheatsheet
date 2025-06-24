# 📦 Node.js

## Introduction

Node.js est un environnement d'exécution JavaScript côté serveur. Il permet de créer des applications rapides et évolutives grâce à son modèle basé sur les événements et son architecture non bloquante.

---

## Commandes essentielles

### Gestion des projets

```bash
npm init -y                          # Initialise un projet avec les paramètres par défaut
npm install <package>                # Installe un package
npm uninstall <package>              # Désinstalle un package
npm update                           # Met à jour les dépendances
```

### Exécution de scripts

```bash
node index.js                        # Exécute un fichier JavaScript
node --inspect index.js              # Exécute avec le mode débogage
```

---

## Exemples pratiques

### Exemple de serveur HTTP simple

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello, Node.js!');
});

server.listen(3000, () => {
  console.log('Server running at http://localhost:3000/');
});
```

### Utilisation d'Express.js

Express.js est un framework minimaliste pour créer des applications web avec Node.js.

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello, Express!');
});

app.listen(3000, () => {
  console.log('Server running at http://localhost:3000/');
});
```

### Lecture et écriture de fichiers

```javascript
const fs = require('fs');

// Écriture dans un fichier
fs.writeFileSync('example.txt', 'Hello, File System!');

// Lecture d'un fichier
const data = fs.readFileSync('example.txt', 'utf8');
console.log(data);
```

---

## Bonnes pratiques

1. **Utiliser un gestionnaire de dépendances** : Utilisez `npm` ou `yarn` pour gérer les packages et les scripts.
2. **Gérer les erreurs** : Implémentez une gestion robuste des erreurs pour éviter les plantages.
3. **Utiliser des outils de débogage** : Exploitez `node --inspect` et des outils comme Chrome DevTools pour déboguer votre code.

---

## Liens utiles

- [Documentation officielle Node.js](https://nodejs.org)
- [Tutoriels Node.js](https://www.w3schools.com/nodejs/)
- [Exemples de projets Node.js](https://github.com/nodejs/examples)
