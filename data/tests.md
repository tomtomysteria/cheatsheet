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

## Modèle Arrange-Act-Assert (AAA)

Le modèle **Arrange-Act-Assert (AAA)** est une structure couramment utilisée pour organiser les tests unitaires. Il permet de rendre les tests plus lisibles et compréhensibles en divisant clairement les étapes du test.

### Étapes du Modèle AAA

1. **Arrange (Préparer)** :
   - Configurez tout ce qui est nécessaire pour exécuter le test.
   - Cela inclut la création des objets, la configuration des mocks, et la définition des données d'entrée.

2. **Act (Agir)** :
   - Effectuez l'action principale, comme appeler une méthode ou exécuter une fonction.

3. **Assert (Vérifier)** :
   - Vérifiez que le résultat obtenu correspond au résultat attendu à l'aide d'assertions.

### Exemple avec Jest

```javascript
test('addition de deux nombres', () => {
  // Arrange
  const a = 2;
  const b = 3;

  // Act
  const result = add(a, b);

  // Assert
  expect(result).toBe(5);
});
```

### Exemple avec Pytest

```python
def test_add():
    # Arrange
    a = 2
    b = 3

    # Act
    result = add(a, b)

    # Assert
    assert result == 5
```

### Exemple avec JUnit

```java
@Test
void shouldAddTwoNumbers() {
    // Arrange
    int a = 2;
    int b = 3;

    // Act
    int result = Calculator.add(a, b);

    // Assert
    assertEquals(5, result);
}
```

### Avantages du Modèle AAA

- **Lisibilité** : Les étapes sont clairement séparées, ce qui rend le test facile à comprendre.
- **Organisation** : Facilite la structuration des tests, surtout dans des scénarios complexes.
- **Débogage** : Permet d'identifier rapidement où se situe un problème (préparation, action ou vérification).

---

## Mocks et Données Factices

### Qu'est-ce qu'un Mock ?

Un **mock** est un objet simulé utilisé dans les tests unitaires pour remplacer une dépendance réelle. Il permet de tester une unité de code (comme une méthode ou une classe) de manière isolée, sans avoir à dépendre de l'implémentation réelle des autres composants.

#### Pourquoi utiliser un mock ?

1. **Isolation** : Les mocks permettent de tester une unité de code sans dépendre des autres parties du système.
2. **Contrôle** : Ils permettent de contrôler le comportement des dépendances (par exemple, en simulant des retours spécifiques ou des exceptions).
3. **Performance** : Les mocks évitent d'utiliser des ressources réelles (comme une base de données ou un service externe), ce qui rend les tests plus rapides.
4. **Fiabilité** : Ils permettent de tester des scénarios difficiles à reproduire avec des dépendances réelles (comme des erreurs réseau).

#### Exemple avec Mockito

Supposons que vous testez un service qui dépend d'un dépôt (repository) pour accéder aux données.

##### Code réel

```java
@Service
public class ProductService {
    private final ProductRepository productRepository;

    public ProductService(ProductRepository productRepository) {
        this.productRepository = productRepository;
    }

    public Product createProduct(Product product) {
        return productRepository.save(product);
    }
}
```

##### Test avec Mock

```java
@ExtendWith(MockitoExtension.class)
public class ProductServiceTest {

    @Mock
    private ProductRepository productRepository;

    @InjectMocks
    private ProductService productService;

    @Test
    void shouldCreateProductSuccessfully() {
        // Arrange
        Product product = new Product(null, "Product A", 100.0);
        Mockito.when(productRepository.save(product)).thenReturn(new Product(1L, "Product A", 100.0));

        // Act
        Product createdProduct = productService.createProduct(product);

        // Assert
        assertNotNull(createdProduct);
        assertEquals(1L, createdProduct.getId());
        assertEquals("Product A", createdProduct.getName());
    }
}
```

#### Fonctionnement

1. **Création du mock** : `@Mock` crée un objet simulé pour `ProductRepository`.
2. **Injection des mocks** : `@InjectMocks` injecte le mock dans `ProductService`.
3. **Définition du comportement** : `when(...).thenReturn(...)` configure le mock pour retourner une valeur spécifique.
4. **Vérification** : `verify(...)` vérifie que le mock a été utilisé comme prévu.

En résumé, un mock est un outil puissant pour tester des unités de code de manière isolée, en simulant leurs dépendances.

### Différence entre Mock et Données Factices

- **Mock** :
  - Simule le comportement d'une dépendance réelle.
  - Permet de contrôler les retours et les exceptions.
  - Utilisé pour tester une unité de code en isolation.

- **Données Factices** :
  - Représentent des données statiques ou préconfigurées.
  - Utilisées pour tester des scénarios spécifiques sans dépendre d'une base de données ou d'une API.
  - Ne simulent pas le comportement des dépendances, mais fournissent des valeurs fixes.

#### Exemple de Données Factices

```java
public class FakeData {
    public static Product getFakeProduct() {
        return new Product(1L, "Fake Product", 50.0);
    }
}

@Test
void shouldUseFakeData() {
    Product fakeProduct = FakeData.getFakeProduct();
    assertEquals("Fake Product", fakeProduct.getName());
}
```

### Créer des Données Factices

- **Qu'est-ce que des données factices ?**
  - Ce sont des objets réels créés pour servir de données d'entrée ou de résultats attendus dans un test.
  - Par exemple, un objet `Product` ou `Category` utilisé dans un test.

- **Pourquoi utiliser des données factices ?**
  - Fournir des données nécessaires pour exécuter le test.
  - Vérifier que les résultats produits par le code testé sont corrects.

- **Exemple** :

```java
Product product = new Product(1L, "Chaise", 59.99, "Comfortable chair", 10);
```

### Résumé

- **Mocker** : Simuler une dépendance (repository, service, etc.).
- **Données factices** : Créer des objets réels pour les utiliser dans les tests.

Il est important de ne pas confondre ces deux concepts pour écrire des tests unitaires efficaces et lisibles.

---

## Liens utiles

- [Documentation Jest](https://jestjs.io/docs)
- [Documentation Pytest](https://docs.pytest.org/en/latest/)
- [Documentation JUnit](https://junit.org/junit5/docs/current/user-guide/)
- [Documentation Cypress](https://docs.cypress.io/)
- [Tutoriels sur les tests](https://www.tutorialspoint.com/software_testing/index.htm)
