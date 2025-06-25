# 📦 Yarn

## Introduction

Yarn est un gestionnaire de paquets rapide et fiable pour JavaScript. Il offre des fonctionnalités avancées comme la gestion des dépendances en parallèle, le verrouillage des versions, et une meilleure sécurité. Il est une alternative populaire à npm, offrant des améliorations en termes de performance et de gestion des dépendances.

---

## Concepts clés

### Pourquoi utiliser Yarn ?

1. **Performance** : Yarn installe les dépendances en parallèle, ce qui accélère le processus.
2. **Fiabilité** : Le fichier `yarn.lock` garantit que les versions des dépendances restent cohérentes entre les environnements.
3. **Sécurité** : Yarn vérifie l'intégrité des paquets téléchargés pour éviter les modifications malveillantes.
4. **Flexibilité** : Yarn prend en charge les monorepos via `workspaces`.

### Enjeux pour les développeurs

1. **Gestion des dépendances** : Assurez-vous que les versions des paquets sont cohérentes entre les environnements.
2. **Automatisation** : Utilisez les scripts définis dans `package.json` pour automatiser les tâches courantes.
3. **Sécurité** : Analysez régulièrement les dépendances pour détecter les vulnérabilités.

---

## Commandes essentielles

### Initialisation et gestion de projet

```bash
yarn init                              # Initialise un projet
yarn add <package>                     # Ajoute un package
yarn add <package>@<version>           # Ajoute une version spécifique d'un package
yarn remove <package>                  # Supprime un package
yarn upgrade                           # Met à jour les dépendances
yarn upgrade-interactive               # Met à jour les dépendances via une interface interactive
yarn install                           # Installe toutes les dépendances définies dans package.json
```

### Gestion des scripts

```bash
yarn run <script>                      # Exécute un script défini dans package.json
yarn test                              # Exécute le script de test
yarn start                             # Exécute le script de démarrage
yarn build                             # Exécute le script de build
```

### Gestion des dépendances

```bash
yarn list                              # Liste les dépendances installées
yarn outdated                          # Liste les dépendances obsolètes
yarn audit                             # Analyse les vulnérabilités des dépendances
yarn why <package>                     # Explique pourquoi un package est installé
```

### Monorepos avec Workspaces

```bash
yarn workspaces info                   # Affiche les informations sur les workspaces
yarn workspace <workspace-name> <command> # Exécute une commande dans un workspace spécifique
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
    "build": "webpack",
    "lint": "eslint ."
  },
  "dependencies": {
    "react": "^18.0.0",
    "axios": "^0.27.0"
  },
  "devDependencies": {
    "jest": "^29.0.0",
    "eslint": "^8.0.0"
  }
}
```

### Installation de dépendances

```bash
yarn add react                        # Installe une dépendance en production
yarn add jest --dev                   # Installe une dépendance en développement
yarn add lodash@4.17.21               # Installe une version spécifique de lodash
```

### Exécution de scripts

```bash
yarn run build                        # Exécute le script de build
yarn run lint                         # Exécute le script de lint
yarn run test                         # Exécute les tests
```

### Monorepos avec Workspaces

```bash
yarn workspaces info                  # Affiche les informations sur les workspaces
yarn workspace my-app add react       # Ajoute une dépendance dans un workspace spécifique
```

---

## Bonnes pratiques

1. **Versionner `package.json` et `yarn.lock`** : Ajoutez ces fichiers au contrôle de version pour garantir la cohérence des dépendances.
2. **Utiliser des scripts personnalisés** : Définissez des scripts dans `package.json` pour automatiser les tâches courantes.
3. **Analyser les vulnérabilités** : Utilisez `yarn audit` régulièrement pour identifier et corriger les problèmes de sécurité.
4. **Utiliser les workspaces** : Simplifiez la gestion des dépendances dans les monorepos avec les workspaces.
5. **Nettoyer les dépendances inutilisées** : Supprimez les dépendances inutilisées avec `yarn remove`.

---

## Outils utiles

- **Yarn Workspaces** : Simplifie la gestion des monorepos.
- **Yarn Audit** : Analyse les vulnérabilités des dépendances.
- **Yarn Upgrade Interactive** : Met à jour les dépendances via une interface interactive.

---

## Commandes avancées

### Débogage et diagnostic

```bash
yarn why <package>                     # Explique pourquoi un package est installé
yarn check                             # Vérifie l'intégrité des dépendances
yarn cache clean                       # Nettoie le cache Yarn
```

### Gestion des versions

```bash
yarn upgrade                           # Met à jour toutes les dépendances
yarn upgrade-interactive               # Met à jour les dépendances via une interface interactive
```

### Monorepos avec Workspaces

```bash
yarn workspaces info                   # Affiche les informations sur les workspaces
yarn workspace <workspace-name> <command> # Exécute une commande dans un workspace spécifique
```

---

## Liens utiles

- [Documentation officielle Yarn](https://yarnpkg.com)
- [Tutoriels Yarn](https://classic.yarnpkg.com/en/docs/getting-started)
- [Exemples de projets Yarn](https://github.com/yarnpkg/examples)
- [Yarn Workspaces](https://classic.yarnpkg.com/en/docs/workspaces/)
