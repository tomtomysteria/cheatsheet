# 📦 Coverage

## Introduction

La couverture de code mesure le pourcentage de code testé par les suites de tests. Elle permet de s'assurer que les tests couvrent toutes les parties critiques du projet, réduisant ainsi les risques de bugs non détectés.

---

## Commandes essentielles

### Jest

```bash
jest --coverage            # Génère un rapport de couverture de code
jest --watch --coverage    # Génère un rapport en mode veille
```

### NYC (Istanbul)

```bash
nyc npm test               # Exécute les tests et génère un rapport de couverture
nyc report                 # Génère un rapport à partir des fichiers de couverture
nyc check-coverage         # Vérifie si les seuils de couverture sont respectés
```

---

## Exemples pratiques

### Configuration Jest pour la couverture

Ajoutez cette configuration dans `jest.config.js` pour activer la couverture de code.

```javascript
module.exports = {
  collectCoverage: true,
  coverageDirectory: "coverage",
  coverageThreshold: {
    global: {
      branches: 80,
      functions: 80,
      lines: 80,
      statements: 80,
    },
  },
};
```

### Utilisation de NYC avec Mocha

Ajoutez NYC pour générer un rapport de couverture avec Mocha.

```bash
npm install --save-dev nyc mocha
nyc mocha
```

---

## Bonnes pratiques

1. **Définir des seuils de couverture** : Configurez des seuils minimaux pour garantir une couverture suffisante.
2. **Analyser les zones non couvertes** : Identifiez les parties du code non couvertes et ajoutez des tests.
3. **Automatiser les rapports** : Intégrez la génération de rapports dans vos pipelines CI/CD.

---

## Liens utiles

- [Documentation Jest Coverage](https://jestjs.io/docs/coverage)
- [Documentation NYC](https://github.com/istanbuljs/nyc)
- [Guide sur la couverture de code](https://www.coverage.io/)
