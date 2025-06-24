# 📦 Tests

## Introduction

Les tests sont essentiels pour garantir la qualité et la fiabilité des applications. Ils permettent de détecter les bugs, de valider les fonctionnalités, et d'assurer la maintenabilité du code.

---

## Commandes essentielles

### Jest (JavaScript/TypeScript)

```bash
jest --watch                          # Exécute les tests en mode veille
jest --coverage                       # Génère un rapport de couverture de code
jest --runInBand                      # Exécute les tests séquentiellement
```

### Pytest (Python)

```bash
pytest                                # Exécute tous les tests
pytest --maxfail=1                    # Arrête après le premier échec
pytest --cov=src                      # Génère un rapport de couverture
```

### JUnit (Java)

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

---

## Bonnes pratiques

1. **Écrire des tests unitaires** : Testez chaque fonction ou méthode individuellement.
2. **Utiliser des tests d'intégration** : Validez les interactions entre les différents modules.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour détecter les régressions rapidement.
4. **Analyser la couverture** : Utilisez des outils comme Jest, Pytest, ou JaCoCo pour mesurer la couverture de code.

---

## Liens utiles

- [Documentation Jest](https://jestjs.io/docs)
- [Documentation Pytest](https://docs.pytest.org/en/latest/)
- [Documentation JUnit](https://junit.org/junit5/docs/current/user-guide/)
- [Tutoriels sur les tests](https://www.tutorialspoint.com/software_testing/index.htm)
