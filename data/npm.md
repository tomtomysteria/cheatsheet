# 📦 NPM

## Introduction

NPM (Node Package Manager) est le gestionnaire de paquets par défaut pour Node.js. Il permet d'installer, de gérer et de partager des bibliothèques JavaScript, facilitant ainsi le développement d'applications.

---

## Commandes essentielles

### Initialisation et gestion de projet

```bash
npm init -y                          # Initialise un projet avec les paramètres par défaut
npm install <package>                # Installe un package
npm uninstall <package>              # Désinstalle un package
npm update                           # Met à jour les dépendances
npm list                             # Liste les dépendances installées
```

### Gestion des scripts

```bash
npm run <script>                     # Exécute un script défini dans package.json
npm test                             # Exécute le script de test
npm start                            # Exécute le script de démarrage
```

### Gestion des versions

```bash
npm version patch                    # Incrémente la version (patch, minor, major)
npm outdated                         # Liste les dépendances obsolètes
npm audit                            # Analyse les vulnérabilités des dépendances
npm audit fix                        # Corrige automatiquement les vulnérabilités
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
    "express": "^4.18.2"
  },
  "devDependencies": {
    "jest": "^29.0.0"
  }
}
```

### Installation de dépendances

```bash
npm install express                  # Installe une dépendance en production
npm install jest --save-dev          # Installe une dépendance en développement
```

### Exécution de scripts

```bash
npm run build                        # Exécute le script de build
npm run test                         # Exécute les tests
```

---

## Bonnes pratiques

1. **Versionner `package.json` et `package-lock.json`** : Ajoutez ces fichiers au contrôle de version pour garantir la cohérence des dépendances.
2. **Utiliser des scripts personnalisés** : Définissez des scripts dans `package.json` pour automatiser les tâches courantes.
3. **Analyser les vulnérabilités** : Utilisez `npm audit` régulièrement pour identifier et corriger les problèmes de sécurité.

---

## Liens utiles

- [Documentation officielle NPM](https://docs.npmjs.com)
- [Guide NPM](https://docs.npmjs.com/getting-started)
- [Exemples de projets NPM](https://github.com/npm/npm-examples)
