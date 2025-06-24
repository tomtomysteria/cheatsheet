# 📦 Yarn

## Introduction

Yarn est un gestionnaire de paquets rapide et fiable pour JavaScript. Il offre des fonctionnalités avancées comme la gestion des dépendances en parallèle, le verrouillage des versions, et une meilleure sécurité.

---

## Commandes essentielles

### Initialisation et gestion de projet

```bash
yarn init                              # Initialise un projet
yarn add <package>                     # Ajoute un package
yarn remove <package>                  # Supprime un package
yarn upgrade                           # Met à jour les dépendances
```

### Gestion des scripts

```bash
yarn run <script>                      # Exécute un script défini dans package.json
yarn test                              # Exécute le script de test
yarn start                             # Exécute le script de démarrage
```

### Gestion des dépendances

```bash
yarn list                              # Liste les dépendances installées
yarn outdated                          # Liste les dépendances obsolètes
yarn audit                             # Analyse les vulnérabilités des dépendances
```

---

## Exemples pratiques

### Exemple de fichier `package.json`

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "scripts": {
    "start": "node index.js",
    "test": "jest",
    "build": "webpack"
  },
  "dependencies": {
    "react": "^18.0.0",
    "axios": "^0.27.0"
  },
  "devDependencies": {
    "jest": "^29.0.0"
  }
}
```

### Installation de dépendances

```bash
yarn add react                        # Installe une dépendance en production
yarn add jest --dev                   # Installe une dépendance en développement
```

### Exécution de scripts

```bash
yarn run build                        # Exécute le script de build
yarn run test                         # Exécute les tests
```

---

## Bonnes pratiques

1. **Versionner `package.json` et `yarn.lock`** : Ajoutez ces fichiers au contrôle de version pour garantir la cohérence des dépendances.
2. **Utiliser des scripts personnalisés** : Définissez des scripts dans `package.json` pour automatiser les tâches courantes.
3. **Analyser les vulnérabilités** : Utilisez `yarn audit` régulièrement pour identifier et corriger les problèmes de sécurité.

---

## Liens utiles

- [Documentation officielle Yarn](https://yarnpkg.com)
- [Tutoriels Yarn](https://classic.yarnpkg.com/en/docs/getting-started)
- [Exemples de projets Yarn](https://github.com/yarnpkg/examples)
