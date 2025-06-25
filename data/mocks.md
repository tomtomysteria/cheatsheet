# 📦 Mocks

## Introduction

Les mocks sont des objets ou fonctions simulées utilisées pour remplacer des dépendances réelles dans les tests. Ils permettent de tester des unités de code de manière isolée en contrôlant les comportements des dépendances. Les mocks sont essentiels pour garantir que les tests sont indépendants des services externes ou des ressources réelles.

---

## Concepts clés

### Pourquoi utiliser des mocks ?

1. **Isolation des tests** : Les mocks permettent de tester une unité de code sans dépendre de services externes comme des API ou des bases de données.
2. **Contrôle des comportements** : Ils permettent de simuler des réponses spécifiques pour les dépendances, comme des erreurs ou des résultats attendus.
3. **Réduction des coûts** : Les mocks évitent d'utiliser des ressources réelles, ce qui est particulièrement utile pour les services payants ou les environnements de production.
4. **Tests rapides** : Les mocks accélèrent les tests en remplaçant les appels réseau ou les opérations coûteuses par des réponses instantanées.

### Types de mocks

1. **Fonctions simulées** : Remplacement de fonctions réelles par des versions simulées.
2. **Objets simulés** : Création d'objets avec des comportements définis pour remplacer des dépendances complexes.
3. **Modules simulés** : Remplacement de modules entiers par des versions simulées.
4. **Spies** : Surveillance des appels à des fonctions existantes sans les remplacer.

---

## Commandes utiles

### Jest

```bash
jest --watch                          # Exécute les tests en mode veille
jest --coverage                       # Génère un rapport de couverture
jest --verbose                        # Affiche des détails sur les tests exécutés
```

### Sinon.js

```bash
npm install sinon                     # Installe Sinon.js
node script.js                        # Exécute un script utilisant Sinon.js
```

---

## Exemples pratiques

### Exemple de mock avec Jest

```javascript
const mockService = {
  getUser: jest.fn().mockResolvedValue({ id: 1, name: 'Alice' }),
};

test('should fetch user', async () => {
  const user = await mockService.getUser();
  expect(user.name).toBe('Alice');
});
```

### Exemple de spy avec Sinon.js

```javascript
const sinon = require('sinon');

const userService = {
  getUser: (id) => ({ id, name: 'Alice' }),
};

const spy = sinon.spy(userService, 'getUser');

userService.getUser(1);
console.log(spy.calledWith(1)); // true
```

### Exemple de module simulé avec Jest

```javascript
jest.mock('./userService', () => ({
  getUser: jest.fn().mockResolvedValue({ id: 1, name: 'Alice' }),
}));

const userService = require('./userService');

test('should fetch mocked user', async () => {
  const user = await userService.getUser();
  expect(user.name).toBe('Alice');
});
```

---

## Bonnes pratiques

1. **Limiter les mocks** : Mockez uniquement les dépendances nécessaires pour éviter les tests trop complexes ou difficiles à maintenir.
2. **Utiliser des outils dédiés** : Intégrez des bibliothèques comme Jest ou Sinon.js pour gérer les mocks de manière efficace.
3. **Documenter les mocks** : Expliquez leur rôle et leur comportement attendu dans les commentaires ou la documentation des tests.
4. **Nettoyer les mocks** : Réinitialisez les mocks après chaque test pour éviter les interférences entre les tests.

   ```javascript
   afterEach(() => {
     jest.clearAllMocks();
   });
   ```

5. **Tester les cas limites** : Simulez des erreurs ou des comportements inattendus pour garantir la robustesse du code.

---

## Outils utiles

- **Jest** : Framework de test avec support intégré pour les mocks.
- **Sinon.js** : Bibliothèque pour créer des spies, stubs, et mocks.
- **Mock Service Worker (MSW)** : Simule des API REST ou GraphQL pour les tests.
- **Nock** : Simule des appels HTTP pour les tests Node.js.

---

## Liens utiles

- [Documentation Jest Mocks](https://jestjs.io/docs/mock-functions)
- [Sinon.js](https://sinonjs.org/)
- [Mock Service Worker](https://mswjs.io/)
- [Nock](https://github.com/nock/nock)
- [Tutoriels sur les mocks](https://www.tutorialspoint.com/software_testing/mock_testing.htm)
