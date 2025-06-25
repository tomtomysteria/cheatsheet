# 📦 NPM

## Introduction

NPM (Node Package Manager) est le gestionnaire de paquets par défaut pour Node.js. Il permet d'installer, de gérer et de partager des bibliothèques JavaScript, facilitant ainsi le développement d'applications. NPM est également utilisé pour gérer les scripts et les dépendances dans les projets JavaScript modernes.

---

## Concepts clés

### Pourquoi utiliser NPM ?

1. **Gestion des dépendances** : NPM simplifie l'installation, la mise à jour et la suppression des bibliothèques nécessaires à un projet.
2. **Automatisation** : Les scripts définis dans `package.json` permettent d'automatiser les tâches courantes comme les tests, le build, ou le déploiement.
3. **Écosystème riche** : NPM offre un accès à des millions de packages via son registre public.
4. **Versionnement** : Le fichier `package-lock.json` garantit la cohérence des versions des dépendances entre les environnements.

### Enjeux pour les développeurs

1. **Sécurité** : Analysez régulièrement les dépendances pour détecter les vulnérabilités.
2. **Performance** : Optimisez les scripts et les dépendances pour réduire les temps de build et d'exécution.
3. **Interopérabilité** : Assurez-vous que les versions des dépendances sont compatibles entre les environnements.

---

## Commandes essentielles

### Initialisation et gestion de projet

```bash
npm init -y                          # Initialise un projet avec les paramètres par défaut
npm install <package>                # Installe un package
npm install <package>@<version>      # Installe une version spécifique d'un package
npm uninstall <package>              # Désinstalle un package
npm update                           # Met à jour les dépendances
npm list                             # Liste les dépendances installées
npm prune                            # Supprime les dépendances inutilisées
```

### Gestion des scripts

```bash
npm run <script>                     # Exécute un script défini dans package.json
npm test                             # Exécute le script de test
npm start                            # Exécute le script de démarrage
npm build                            # Exécute le script de build
npm lint                             # Exécute le script de lint
```

### Gestion des versions

```bash
npm version patch                    # Incrémente la version (patch, minor, major)
npm outdated                         # Liste les dépendances obsolètes
npm audit                            # Analyse les vulnérabilités des dépendances
npm audit fix                        # Corrige automatiquement les vulnérabilités
```

### Gestion du cache

```bash
npm cache verify                     # Vérifie l'intégrité du cache
npm cache clean --force              # Nettoie le cache NPM
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
    "express": "^4.18.2",
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
npm install express                  # Installe une dépendance en production
npm install jest --save-dev          # Installe une dépendance en développement
npm install lodash@4.17.21           # Installe une version spécifique de lodash
```

### Exécution de scripts

```bash
npm run build                        # Exécute le script de build
npm run lint                         # Exécute le script de lint
npm run test                         # Exécute les tests
```

---

## Bonnes pratiques

1. **Versionner `package.json` et `package-lock.json`** : Ajoutez ces fichiers au contrôle de version pour garantir la cohérence des dépendances.
2. **Utiliser des scripts personnalisés** : Définissez des scripts dans `package.json` pour automatiser les tâches courantes.
3. **Analyser les vulnérabilités** : Utilisez `npm audit` régulièrement pour identifier et corriger les problèmes de sécurité.
4. **Nettoyer les dépendances inutilisées** : Supprimez les dépendances inutilisées avec `npm prune`.
5. **Documenter les scripts** : Ajoutez des commentaires dans `package.json` pour expliquer les scripts complexes.

---

## Outils utiles

- **NPM Audit** : Analyse les vulnérabilités des dépendances.
- **NPM Cache** : Optimise les installations en réutilisant les paquets déjà téléchargés.
- **NPM Scripts** : Simplifie l'automatisation des tâches courantes.

---

## Commandes avancées

### Débogage et diagnostic

```bash
npm ls <package>                     # Liste les dépendances d'un package spécifique
npm dedupe                           # Supprime les doublons dans les dépendances
npm doctor                           # Analyse l'environnement pour détecter les problèmes
```

### Gestion des versions

```bash
npm shrinkwrap                       # Crée un fichier de verrouillage des dépendances (alternative à package-lock.json)
npm ci                               # Installe les dépendances en respectant strictement le fichier package-lock.json
```

### Gestion du cache

```bash
npm cache verify                     # Vérifie l'intégrité du cache
npm cache clean --force              # Nettoie le cache NPM
```

---

## Liens utiles

- [Documentation officielle NPM](https://docs.npmjs.com)
- [Guide NPM](https://docs.npmjs.com/getting-started)
- [Exemples de projets NPM](https://github.com/npm/npm-examples)
- [NPM Audit](https://docs.npmjs.com/cli/v8/commands/npm-audit)
