# 📦 Prettier

## Introduction

Prettier est un formateur de code qui garantit un style de code cohérent dans les projets. Il prend en charge plusieurs langages, notamment JavaScript, TypeScript, HTML, CSS, JSON, et bien d'autres. Prettier est largement utilisé pour automatiser le formatage du code et améliorer la lisibilité.

---

## Pourquoi utiliser Prettier ?

1. **Style de code cohérent** : Prettier applique des règles de formatage uniformes à tout le projet.
2. **Automatisation** : Élimine les discussions sur le style de code en automatisant le formatage.
3. **Compatibilité** : Fonctionne avec de nombreux langages et outils.
4. **Intégration facile** : Peut être intégré dans les éditeurs de code, les pipelines CI/CD, et les scripts NPM.

---

## Installation

### Étapes pour installer Prettier

1. Installez Prettier globalement ou localement dans un projet :

```bash
npm install --save-dev prettier
```

2. Vérifiez l'installation :

```bash
npx prettier --version
```

---

## Configuration

### Exemple de fichier `.prettierrc`

```json
{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5",
  "printWidth": 80
}
```

### Exemple de fichier `.prettierignore`

Ignorez certains fichiers ou répertoires :

```
node_modules
dist
build
*.min.js
```

---

## Utilisation

### Commandes essentielles

```bash
npx prettier <file>                     # Formate un fichier spécifique
npx prettier <directory> --write        # Formate tous les fichiers d'un répertoire
npx prettier <file> --check             # Vérifie si le fichier est correctement formaté
npx prettier <directory> --list-different # Liste les fichiers non formatés
```

### Intégration dans les scripts NPM

Ajoutez un script dans `package.json` :

```json
{
  "scripts": {
    "format": "prettier --write src/**/*.js",
    "check-format": "prettier --check src/**/*.js"
  }
}
```

Exécutez les scripts :

```bash
npm run format
npm run check-format
```

---

## Intégration dans les éditeurs

### Visual Studio Code

1. Installez l'extension **Prettier - Code formatter**.
2. Configurez Prettier comme formateur par défaut :
   - Allez dans les paramètres (`Ctrl + ,`).
   - Recherchez `Editor: Default Formatter` et sélectionnez `Prettier`.
3. Activez le formatage automatique à l'enregistrement :
   - Recherchez `Editor: Format On Save` et cochez la case.

---

## Bonnes pratiques

1. **Automatiser le formatage** : Intégrez Prettier dans les pipelines CI/CD pour garantir un style de code cohérent.
2. **Utiliser un fichier `.prettierrc`** : Centralisez les règles de formatage pour tout le projet.
3. **Ignorer les fichiers inutiles** : Ajoutez un fichier `.prettierignore` pour exclure les fichiers générés ou volumineux.
4. **Combiner avec ESLint** : Utilisez Prettier avec ESLint pour gérer à la fois le formatage et les règles de qualité du code.
5. **Documenter les conventions** : Ajoutez une section dans la documentation du projet pour expliquer les règles de formatage.

---

## Enjeux et concepts avancés

### Enjeux

1. **Standardisation du code** : Garantir un style uniforme dans les équipes de développement, réduisant les erreurs et améliorant la lisibilité.
2. **Collaboration efficace** : Faciliter les revues de code en éliminant les discussions sur le style.
3. **Productivité accrue** : Réduire le temps passé à corriger manuellement le formatage.

### Concepts avancés

1. **Conflits avec ESLint** : Prettier peut entrer en conflit avec certaines règles d'ESLint. Utilisez `eslint-config-prettier` pour désactiver les règles de formatage d'ESLint.
2. **Hooks Git** : Automatisez le formatage avec des hooks comme `pre-commit` pour garantir que le code est formaté avant d'être poussé.
3. **Intégration CI/CD** : Ajoutez Prettier dans les pipelines CI/CD pour vérifier le formatage automatiquement.

---

## Commandes utiles supplémentaires

### Commandes avancées

```bash
npx prettier --debug-check                # Affiche des informations de débogage sur le formatage
npx prettier --find-config-path <file>    # Trouve le chemin du fichier de configuration utilisé
npx prettier --help                       # Affiche l'aide et les options disponibles
```

### Utilisation avec des fichiers spécifiques

```bash
npx prettier "src/**/*.js" --write       # Formate tous les fichiers JavaScript dans le dossier src
npx prettier "src/**/*.{js,ts}" --check  # Vérifie le formatage des fichiers JS et TS
```

---

## Bonnes pratiques avancées

1. **Configurer des hooks Git** : Utilisez des outils comme `husky` pour exécuter Prettier avant les commits.
2. **Automatisation CI/CD** : Ajoutez des étapes de vérification de formatage dans les pipelines CI/CD pour éviter les erreurs de style.
3. **Documentation interne** : Expliquez les règles de formatage dans la documentation du projet pour faciliter l'adoption.
4. **Formation des équipes** : Sensibilisez les développeurs à l'importance du formatage automatique pour améliorer la collaboration.

---

## Liens utiles

- [Documentation officielle Prettier](https://prettier.io/docs/en/)
- [Tutoriels Prettier](https://www.tutorialspoint.com/prettier/index.htm)
- [Exemples de configuration Prettier](https://github.com/prettier/prettier)
- [Extension VS Code Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [Guide d'intégration Prettier et ESLint](https://prettier.io/docs/en/integrating-with-linters.html)
- [Guide de configuration avancée](https://prettier.io/docs/en/options.html)
- [Intégration avec Husky](https://typicode.github.io/husky/#/)
- [Exemples de pipelines CI/CD avec Prettier](https://github.com/prettier/prettier-ci)
- [Comparaison ESLint vs Prettier](https://eslint.org/docs/latest/user-guide/integrations#prettier)
