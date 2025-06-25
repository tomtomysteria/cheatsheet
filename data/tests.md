# 📦 Tests

## Introduction

Les tests sont essentiels pour garantir la qualité et la fiabilité des applications. Ils permettent de détecter les bugs, de valider les fonctionnalités, et d'assurer la maintenabilité du code. Les tests peuvent être classés en plusieurs catégories, chacune ayant un rôle spécifique dans le cycle de développement.

---

## Types de tests

### Tests unitaires

Les tests unitaires valident le comportement des fonctions ou méthodes individuelles. Ils sont rapides à exécuter et permettent de détecter les bugs au niveau des composants isolés.

### Tests d'intégration

Les tests d'intégration vérifient que les différents modules ou services fonctionnent correctement ensemble. Ils permettent de valider les interactions entre les composants.

### Tests fonctionnels

Les tests fonctionnels valident les fonctionnalités de l'application du point de vue de l'utilisateur. Ils simulent des scénarios réels pour s'assurer que l'application répond aux exigences.

### Tests de bout en bout (E2E)

Les tests E2E simulent des interactions utilisateur complètes pour valider le fonctionnement global de l'application.

### Tests de performance

Les tests de performance mesurent la rapidité, la scalabilité et la stabilité de l'application sous différentes charges.

### Tests de sécurité

Les tests de sécurité identifient les vulnérabilités dans l'application, comme les failles XSS, CSRF, ou les injections SQL.

---

## Frameworks de tests

### JavaScript/TypeScript

#### Jest

Jest est un framework de test populaire pour JavaScript et TypeScript. Il prend en charge les tests unitaires, d'intégration, et de couverture.

```bash
jest --watch                          # Exécute les tests en mode veille
jest --coverage                       # Génère un rapport de couverture de code
jest --runInBand                      # Exécute les tests séquentiellement
```

#### Mocha

Mocha est un framework de test flexible pour JavaScript. Il est souvent utilisé avec Chai pour les assertions.

```bash
mocha                                 # Exécute les tests
mocha --reporter spec                 # Utilise un format de rapport spécifique
```

#### Cypress

Cypress est un outil puissant pour les tests de bout en bout. Il permet de simuler des interactions utilisateur dans un navigateur.

```bash
cypress open                          # Ouvre l'interface graphique de Cypress
cypress run                           # Exécute les tests en mode terminal
```

### Python

#### Pytest

Pytest est un framework de test puissant pour Python. Il prend en charge les tests unitaires, d'intégration, et de couverture.

```bash
pytest                                # Exécute tous les tests
pytest --maxfail=1                    # Arrête après le premier échec
pytest --cov=src                      # Génère un rapport de couverture
```

### Java

#### JUnit

JUnit est un framework de test standard pour Java. Il est utilisé pour les tests unitaires et d'intégration.

```bash
mvn test                              # Exécute les tests avec Maven
mvn surefire-report:report            # Génère un rapport de tests
```

---

## Exemples pratiques

### Exemple de test avec Jest

```javascript
function add(a, b) {
  return a + b;
}

test('addition de deux nombres', () => {
  expect(add(2, 3)).toBe(5);
});
```

### Exemple de test avec Pytest

```python
def add(a, b):
    return a + b

def test_add():
    assert add(2, 3) == 5
```

### Exemple de test avec JUnit

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class CalculatorTest {
    @Test
    public void testAdd() {
        assertEquals(5, Calculator.add(2, 3));
    }
}
```

### Exemple de test E2E avec Cypress

```javascript
describe('Page d\'accueil', () => {
  it('devrait afficher le titre', () => {
    cy.visit('http://localhost:3000');
    cy.contains('Bienvenue sur mon site').should('be.visible');
  });
});
```

---

## Commandes avancées

### Génération de rapports

#### Jest

```bash
jest --coverage --json --outputFile=coverage.json
```

#### Pytest

```bash
pytest --cov=src --cov-report=html
```

#### JUnit

```bash
mvn surefire-report:report
```

### Tests parallèles

#### Jest

```bash
jest --maxWorkers=4
```

#### Pytest

```bash
pytest -n 4
```

---

## Bonnes pratiques

1. **Écrire des tests unitaires** : Testez chaque fonction ou méthode individuellement.
2. **Utiliser des tests d'intégration** : Validez les interactions entre les différents modules.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour détecter les régressions rapidement.
4. **Analyser la couverture** : Utilisez des outils comme Jest, Pytest, ou JaCoCo pour mesurer la couverture de code.
5. **Documenter les tests** : Ajoutez des commentaires pour expliquer les scénarios de test complexes.
6. **Utiliser des mocks** : Simulez les dépendances externes pour isoler les tests.

---

## Liens utiles

- [Documentation Jest](https://jestjs.io/docs)
- [Documentation Pytest](https://docs.pytest.org/en/latest/)
- [Documentation JUnit](https://junit.org/junit5/docs/current/user-guide/)
- [Documentation Cypress](https://docs.cypress.io/)
- [Tutoriels sur les tests](https://www.tutorialspoint.com/software_testing/index.htm)
