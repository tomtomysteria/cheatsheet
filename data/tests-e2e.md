## Tests End-to-End (E2E)

Les tests E2E permettent de valider le fonctionnement complet d'une application en simulant les interactions utilisateur. Ils sont essentiels pour garantir que toutes les parties de l'application fonctionnent correctement ensemble.

---

### Commandes essentielles

#### Cypress
```bash
npm install cypress                   # Installe Cypress
npx cypress open                      # Ouvre l'interface graphique de Cypress
npx cypress run                       # Exécute les tests en mode headless
```

#### Playwright
```bash
npm install playwright                # Installe Playwright
npx playwright test                   # Exécute les tests Playwright
npx playwright codegen <url>          # Génère des scripts de test interactifs
```

---

### Exemples pratiques

#### Exemple de test avec Cypress
```javascript
describe('Page d\'accueil', () => {
  it('devrait afficher le titre', () => {
    cy.visit('http://localhost:3000');
    cy.contains('Bienvenue sur mon site').should('be.visible');
  });
});
```

#### Exemple de test avec Playwright
```javascript
const { test, expect } = require('@playwright/test');

test('Page d\'accueil', async ({ page }) => {
  await page.goto('http://localhost:3000');
  const title = await page.textContent('h1');
  expect(title).toBe('Bienvenue sur mon site');
});
```

---

### Bonnes pratiques

1. **Utiliser des environnements isolés** : Exécutez les tests E2E dans des environnements dédiés pour éviter les interférences.
2. **Automatiser les tests** : Intégrez les tests E2E dans les pipelines CI/CD pour détecter les régressions rapidement.
3. **Gérer les données de test** : Utilisez des bases de données ou des mocks spécifiques pour les tests E2E.
4. **Tester les scénarios critiques** : Priorisez les tests des fonctionnalités essentielles pour l'utilisateur.

---

### Liens utiles

- [Documentation officielle Cypress](https://docs.cypress.io/)
- [Documentation officielle Playwright](https://playwright.dev/docs/intro)
- [Tutoriels sur les tests E2E](https://www.tutorialspoint.com/software_testing/end_to_end_testing.htm)