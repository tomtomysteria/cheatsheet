# 📦 SonarQube

## Introduction

SonarQube est une plateforme open-source pour l'analyse de la qualité du code. Elle permet de détecter les bugs, les failles de sécurité, le code dupliqué, et les problèmes de maintenabilité. SonarQube est largement utilisé pour améliorer la qualité des projets logiciels et garantir des standards élevés.

---

## Pourquoi utiliser SonarQube ?

1. **Détection des bugs** : Identifie les erreurs potentielles dans le code.
2. **Analyse de sécurité** : Détecte les failles de sécurité et les vulnérabilités.
3. **Code dupliqué** : Repère les duplications de code pour les réduire.
4. **Maintenabilité** : Évalue la complexité du code pour améliorer sa lisibilité et sa maintenabilité.
5. **Intégration CI/CD** : Automatise l'analyse de code dans les pipelines CI/CD.

---

## Installation de SonarQube

### Étapes pour installer SonarQube sur Windows

1. **Télécharger SonarQube** :
   - Téléchargez SonarQube Community Edition depuis [SonarSource](https://www.sonarsource.com/products/sonarqube/downloads/).

2. **Décompresser SonarQube** :
   - Décompressez le fichier téléchargé dans un répertoire de votre choix.

3. **Démarrer SonarQube** :
   - Allez dans le dossier `bin/windows-x86-64`.
   - Exécutez `StartSonar.bat`.

4. **Accéder à l'interface web** :
   - Ouvrez [http://localhost:9000](http://localhost:9000) dans votre navigateur.
   - Connectez-vous avec les identifiants par défaut :
     - **Login** : `admin`
     - **Mot de passe** : `admin`

---

## Configuration de SonarScanner

SonarScanner est l'outil utilisé pour analyser le code source.

### Installation

1. Téléchargez SonarScanner depuis [SonarScanner](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/scanners/sonarscanner/).
2. Ajoutez le chemin de SonarScanner à la variable d'environnement `PATH`.

### Configuration du projet

Créez un fichier `sonar-project.properties` à la racine du projet :

```properties
sonar.projectKey=demo-project
sonar.projectName=Demo Project
sonar.projectVersion=1.0
sonar.sources=src
sonar.java.binaries=target/classes
sonar.host.url=http://localhost:9000
sonar.login=TON_TOKEN
```

---

## Analyse de code

### Étapes pour lancer une analyse

1. Compilez le projet :

   ```bash
   mvn clean install
   ```

2. Lancez SonarScanner :

   ```bash
   sonar-scanner
   ```

### Résultats

Les résultats de l'analyse sont disponibles dans l'interface web de SonarQube ([http://localhost:9000](http://localhost:9000)).

---

## Intégration dans CI/CD

SonarQube peut être intégré dans les pipelines CI/CD pour automatiser l'analyse de code.

### Exemple avec GitLab CI/CD

Ajoutez SonarScanner dans `.gitlab-ci.yml` :

```yaml
stages:
  - build
  - test
  - analyze

analyze:
  script:
    - sonar-scanner
```

---

## Bonnes pratiques

1. **Analyser régulièrement** : Intégrez SonarQube dans les pipelines CI/CD pour une analyse continue.
2. **Fixer des seuils de qualité** : Configurez des seuils pour garantir un niveau minimal de qualité.
3. **Corriger les problèmes critiques** : Priorisez les bugs et failles de sécurité détectés.
4. **Éviter les duplications** : Réduisez le code dupliqué pour améliorer la maintenabilité.
5. **Documenter les règles** : Ajoutez des commentaires pour expliquer les décisions de codage.

---

## Liens utiles

- [Documentation officielle SonarQube](https://www.sonarsource.com/products/sonarqube/)
- [Tutoriels SonarQube](https://www.tutorialspoint.com/sonarqube/index.htm)
- [SonarScanner](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/scanners/sonarscanner/)
- [Exemples de configuration SonarQube](https://github.com/SonarSource/sonarqube)
