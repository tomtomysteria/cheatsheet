# 📦 Coverage

## Introduction

La couverture de code (coverage) mesure le pourcentage de code testé par les suites de tests automatisés (tests unitaires, d'intégration, etc.). Elle permet de s'assurer que les tests couvrent toutes les parties critiques du projet, réduisant ainsi les risques de bugs non détectés. Elle est utilisée pour améliorer la qualité des tests, identifier les zones non couvertes, et garantir que les fonctionnalités essentielles sont correctement validées.

### Plus concrètement

Quand tu écris des tests pour ton code, tu veux t'assurer qu'ils vérifient bien toutes les parties importantes. Le coverage te dit, en pourcentage, combien de ton code a été "visité" (exécuté) pendant l'exécution de ces tests.

### Pourquoi c’est important ?

1. **Détecter du code mort** : Identifier les parties du code qui ne sont jamais exécutées.
2. **Évaluer la qualité des tests** : S'assurer que les tests couvrent les parties critiques du code.
3. **Réduire les bugs cachés** : Minimiser les risques de bugs dans les zones non testées.

### Outils populaires selon les langages

- Python : coverage.py, intégré avec pytest.
- JavaScript/Node.js : Jest, Istanbul, nyc.
- Java : JaCoCo.
- C # : Visual Studio Coverage, Coverlet.

### Attention

Avoir 100% de coverage ne veut pas dire zéro bug ! Tu peux exécuter toutes les lignes sans forcément tester toutes les situations.

---

## Types de coverage

### Coverage des lignes (Line Coverage)

Mesure combien de lignes de code ont été exécutées.

### Coverage des branches (Branch Coverage)

Mesure combien de chemins logiques (ex. `if/else`, `switch`) ont été testés.

### Coverage des fonctions/méthodes

Mesure combien de fonctions ou méthodes ont été appelées.

### Coverage des conditions

Mesure combien de combinaisons de conditions logiques ont été testées.

---

## Exemple concret

### Code source

```python
def diviser(a, b):
    if b == 0:
        return None
    return a / b
```

### Test partiel

```python
def test_diviser():
    assert diviser(10, 2) == 5
```

➡️ Ce test couvre :

- L'appel de la fonction.
- Le cas où `b != 0`.

Mais il ne couvre pas le cas où `b == 0`, donc la couverture est partielle.

---

## Outils de couverture

### Python

#### Coverage.py

Coverage.py est un outil puissant pour mesurer la couverture de code Python.

```bash
coverage run -m pytest                # Exécute les tests avec mesure de couverture
coverage report                       # Affiche un rapport dans le terminal
coverage html                         # Génère un rapport HTML
coverage xml                          # Génère un rapport XML pour CI/CD
```

---

### JavaScript/TypeScript

#### Jest

Jest inclut un outil intégré pour mesurer la couverture de code.

```bash
jest --coverage                       # Génère un rapport de couverture
jest --coverage --json --outputFile=coverage.json # Exporte le rapport en JSON
jest --watch --coverage               # Génère un rapport en mode veille
```

#### Istanbul/NYC

Istanbul est un outil populaire pour mesurer la couverture de code JavaScript.

```bash
npx nyc npm test                      # Exécute les tests et génère un rapport de couverture
npx nyc report --reporter=html        # Génère un rapport HTML
npx nyc check-coverage --lines=80     # Vérifie si les seuils de couverture sont respectés
```

### Utilisation de NYC avec Mocha

Ajoutez NYC pour générer un rapport de couverture avec Mocha.

```bash
npm install --save-dev nyc mocha
nyc mocha
```

---

### Java

#### JaCoCo

JaCoCo est un outil de couverture de code pour les projets Java.

```bash
mvn test                              # Exécute les tests
mvn jacoco:report                     # Génère un rapport de couverture
mvn jacoco:check                      # Vérifie les seuils de couverture
```

---

## Exemples pratiques

### Exemple de configuration Jest

Ajoutez cette configuration dans `jest.config.js` pour activer la couverture de code.

```javascript
// filepath: jest.config.js
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

### Exemple de rapport Coverage.py

```bash
coverage report
```

Rapport généré :

```text
Name               Stmts   Miss  Cover
--------------------------------------
src/main.py          100     10    90%
src/utils.py          50      5    90%
--------------------------------------
TOTAL                150     15    90%
```

### Exemple de rapport JaCoCo

Ajoutez cette configuration dans `pom.xml` pour activer JaCoCo.

```xml
<!-- filepath: pom.xml -->
<plugin>
  <groupId>org.jacoco</groupId>
  <artifactId>jacoco-maven-plugin</artifactId>
  <version>0.8.8</version>
  <executions>
    <execution>
      <goals>
        <goal>prepare-agent</goal>
      </goals>
    </execution>
    <execution>
      <id>report</id>
      <phase>post-integration-test</phase>
      <goals>
        <goal>report</goal>
      </goals>
    </execution>
  </executions>
</plugin>
```

---

## Bonnes pratiques

1. **Intégrer la couverture dans CI/CD** : Configurez les pipelines pour exécuter les tests et générer des rapports de couverture.
2. **Analyser les zones non couvertes** : Identifiez les parties du code non testées et ajoutez des tests pour les couvrir.
3. **Fixer des seuils de couverture** : Définissez des seuils minimaux pour garantir une couverture acceptable (ex. 80%).
4. **Utiliser des rapports visuels** : Exploitez les rapports HTML pour visualiser les zones non couvertes.
5. **Automatiser les rapports** : Exportez les rapports dans des formats compatibles avec des outils de gestion de qualité.
6. **Prioriser les tests critiques** : Concentrez-vous sur les fonctionnalités essentielles et les zones à haut risque.

---

## Liens utiles

- [Documentation Jest Coverage](https://jestjs.io/docs/cli#--coverage)
- [Documentation Istanbul/NYC](https://istanbul.js.org/)
- [Documentation Coverage.py](https://coverage.readthedocs.io/)
- [Documentation JaCoCo](https://www.jacoco.org/jacoco/)
- [Tutoriels sur la couverture de code](https://www.tutorialspoint.com/software_testing/code_coverage.htm)
