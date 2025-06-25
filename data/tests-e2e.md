## Tests End-to-End (E2E)

Les tests E2E permettent de valider le fonctionnement complet d'une application en simulant les interactions utilisateur. Ils sont essentiels pour garantir que toutes les parties de l'application fonctionnent correctement ensemble, depuis l'interface utilisateur jusqu'à la base de données.

---

## Concepts clés

### Pourquoi utiliser les tests E2E ?

1. **Validation complète** : Les tests E2E vérifient que toutes les couches de l'application fonctionnent ensemble (frontend, backend, base de données).
2. **Détection des régressions** : Ils permettent d'identifier les problèmes introduits par des modifications du code.
3. **Simulation utilisateur** : Les tests E2E reproduisent les actions des utilisateurs pour garantir une expérience cohérente.
4. **Automatisation** : Ils peuvent être intégrés dans les pipelines CI/CD pour une exécution régulière.

### Enjeux pour les développeurs

1. **Fiabilité** : Les tests doivent être stables et ne pas échouer à cause de facteurs externes (ex. réseau, données instables).
2. **Performance** : Les tests E2E peuvent être longs à exécuter. Optimisez leur durée en limitant les scénarios inutiles.
3. **Isolation** : Exécutez les tests dans des environnements dédiés pour éviter les interférences avec les données de production.
4. **Maintenance** : Les tests doivent être régulièrement mis à jour pour refléter les changements dans l'application.

---

## Commandes essentielles

### Cypress

```bash
npm install cypress                   # Installe Cypress
npx cypress open                      # Ouvre l'interface graphique de Cypress
npx cypress run                       # Exécute les tests en mode headless
npx cypress run --spec <path>         # Exécute un test spécifique
```

### Playwright

```bash
npm install playwright                # Installe Playwright
npx playwright test                   # Exécute les tests Playwright
npx playwright codegen <url>          # Génère des scripts de test interactifs
npx playwright show-report            # Affiche le rapport des tests
```

### Puppeteer

```bash
npm install puppeteer                 # Installe Puppeteer
node <script.js>                      # Exécute un script Puppeteer
```

---

## Exemples pratiques

### Exemple de test avec Cypress

```javascript
describe('Page d\'accueil', () => {
  it('devrait afficher le titre', () => {
    cy.visit('http://localhost:3000');
    cy.contains('Bienvenue sur mon site').should('be.visible');
  });

  it('devrait permettre de soumettre un formulaire', () => {
    cy.get('input[name="email"]').type('test@example.com');
    cy.get('button[type="submit"]').click();
    cy.contains('Merci pour votre soumission').should('be.visible');
  });
});
```

### Exemple de test avec Playwright

```javascript
const { test, expect } = require('@playwright/test');

test('Page d\'accueil', async ({ page }) => {
  await page.goto('http://localhost:3000');
  const title = await page.textContent('h1');
  expect(title).toBe('Bienvenue sur mon site');
});

test('Soumission de formulaire', async ({ page }) => {
  await page.goto('http://localhost:3000');
  await page.fill('input[name="email"]', 'test@example.com');
  await page.click('button[type="submit"]');
  const confirmation = await page.textContent('.confirmation-message');
  expect(confirmation).toBe('Merci pour votre soumission');
});
```

### Exemple de test avec Puppeteer

```javascript
const puppeteer = require('puppeteer');

(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  await page.goto('http://localhost:3000');
  const title = await page.$eval('h1', el => el.textContent);
  console.log(title); // Affiche "Bienvenue sur mon site"
  await browser.close();
})();
```

---

## Bonnes pratiques

1. **Utiliser des environnements isolés** : Exécutez les tests E2E dans des environnements dédiés pour éviter les interférences avec les données de production.
2. **Automatiser les tests** : Intégrez les tests E2E dans les pipelines CI/CD pour détecter les régressions rapidement.
3. **Gérer les données de test** : Utilisez des bases de données ou des mocks spécifiques pour les tests E2E.
4. **Tester les scénarios critiques** : Priorisez les tests des fonctionnalités essentielles pour l'utilisateur.
5. **Analyser les rapports** : Utilisez les outils intégrés (ex. Cypress Dashboard, Playwright Report) pour identifier les problèmes.
6. **Limiter les dépendances externes** : Mockez les services tiers pour éviter les échecs liés à des problèmes de réseau.

---

## Outils utiles

- **Cypress** : Interface graphique et API puissante pour les tests E2E.
- **Playwright** : Tests multi-navigateurs avec des fonctionnalités avancées.
- **Puppeteer** : Automatisation des navigateurs basés sur Chromium.
- **TestCafe** : Alternative légère pour les tests E2E.
- **Postman** : Test des API REST utilisées dans les scénarios E2E.

---

## Commandes avancées

### Cypress

```bash
npx cypress run --record              # Enregistre les résultats des tests sur le dashboard Cypress
npx cypress run --browser chrome      # Exécute les tests dans un navigateur spécifique
```

### Playwright

```bash
npx playwright test --headed          # Exécute les tests avec une interface visible
npx playwright test --debug           # Exécute les tests en mode débogage
```

### Puppeteer

```javascript
const browser = await puppeteer.launch({ headless: false }); // Lance Puppeteer en mode non headless
```

---

## Liens utiles

- [Documentation officielle Cypress](https://docs.cypress.io/)
- [Documentation officielle Playwright](https://playwright.dev/docs/intro)
- [Documentation officielle Puppeteer](https://pptr.dev/)
- [Tutoriels sur les tests E2E](https://www.tutorialspoint.com/software_testing/end_to_end_testing.htm)
