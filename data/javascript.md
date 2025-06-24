# 📦 JavaScript / TypeScript

## Introduction

JavaScript est un langage de programmation utilisé pour le développement web côté client et côté serveur. TypeScript est un sur-ensemble de JavaScript qui ajoute des types statiques pour améliorer la robustesse et la maintenabilité du code.

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
```

### Exemples pratiques

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "scripts": {
    "start": "node index.js",
    "test": "jest"
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
```

### Exemples pratiques

```bash
yarn add react react-dom
yarn run start
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

### Exemples pratiques

```typescript
function greet(name: string): string {
  return `Hello, ${name}!`;
}

console.log(greet("World"));
```

---

## Liens utiles

- [Documentation JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [Documentation TypeScript](https://www.typescriptlang.org/docs/)
- [Documentation NPM](https://docs.npmjs.com/)
- [Documentation Yarn](https://yarnpkg.com/)
