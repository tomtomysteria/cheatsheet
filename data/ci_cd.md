# 📦 CI/CD

## Introduction

CI/CD (Intégration Continue / Déploiement Continu) est une pratique essentielle pour automatiser le développement, les tests, et le déploiement des applications. Elle permet d'améliorer la qualité du code, de réduire les délais de livraison, et de minimiser les erreurs. CI/CD repose sur des pipelines qui orchestrent les étapes nécessaires pour transformer le code source en une application prête à être déployée.

---

## Concepts clés

### Pourquoi utiliser CI/CD ?

1. **Automatisation** : CI/CD élimine les tâches manuelles répétitives, réduisant les risques d'erreurs humaines.
2. **Qualité du code** : Les tests automatisés garantissent que le code respecte les normes de qualité.
3. **Déploiement rapide** : CI/CD permet de livrer des fonctionnalités rapidement et de manière fiable.
4. **Collaboration** : Facilite le travail en équipe en intégrant les changements de code dans un pipeline centralisé.

### Enjeux pour les développeurs

1. **Fiabilité** : Les pipelines doivent être robustes pour gérer les échecs et les erreurs.
2. **Sécurité** : Protégez les secrets et les clés API utilisés dans les pipelines.
3. **Performance** : Optimisez les étapes du pipeline pour réduire les temps d'exécution.
4. **Scalabilité** : Configurez les pipelines pour gérer des projets de grande envergure avec plusieurs équipes.

---

## Outils CI/CD

### Jenkins

Jenkins est un outil open-source pour l'automatisation des pipelines CI/CD.

```bash
# Commandes essentielles
jenkins --version                   # Vérifie la version de Jenkins
sudo systemctl start jenkins        # Démarre Jenkins
sudo systemctl stop jenkins         # Arrête Jenkins
sudo systemctl restart jenkins      # Redémarre Jenkins
sudo systemctl status jenkins       # Vérifie l'état de Jenkins
```

Exemple de pipeline Jenkinsfile :

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Déploiement en cours..."'
            }
        }
    }
}
```

---

### GitLab CI/CD

GitLab CI/CD est intégré à GitLab pour gérer les pipelines directement dans les projets.

Exemple de fichier `.gitlab-ci.yml` :

```yaml
stages:
  - build
  - test
  - deploy

build:
  script:
    - npm install
    - npm run build

test:
  script:
    - npm test

deploy:
  script:
    - echo "Déploiement en cours..."
```

---

### GitHub Actions

GitHub Actions permet de créer des workflows CI/CD directement dans les dépôts GitHub.

Exemple de fichier `workflow.yml` :

```yaml
name: CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Install dependencies
        run: npm install
      - name: Build
        run: npm run build

  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: npm test

  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy
        run: echo "Déploiement en cours..."
```

---

### Azure DevOps

Azure DevOps est une plateforme complète pour gérer les pipelines CI/CD, les tests, et les déploiements.

Exemple de fichier `azure-pipelines.yml` :

```yaml
trigger:
  - main

pool:
  vmImage: 'ubuntu-latest'

steps:
  - task: NodeTool@0
    inputs:
      versionSpec: '16.x'
    displayName: 'Install Node.js'

  - script: |
      npm install
      npm run build
    displayName: 'Build application'

  - script: |
      npm test
    displayName: 'Run tests'

  - script: |
      echo "Déploiement en cours..."
    displayName: 'Deploy application'
```

---

### AWS CodePipeline

AWS CodePipeline est un service CI/CD pour automatiser les étapes de construction, de test, et de déploiement.

Exemple de configuration JSON pour AWS CodePipeline :

```json
{
  "pipeline": {
    "name": "MyPipeline",
    "roleArn": "arn:aws:iam::123456789012:role/AWSCodePipelineServiceRole",
    "stages": [
      {
        "name": "Source",
        "actions": [
          {
            "name": "SourceAction",
            "actionTypeId": {
              "category": "Source",
              "owner": "AWS",
              "provider": "S3",
              "version": "1"
            },
            "outputArtifacts": [
              {
                "name": "SourceArtifact"
              }
            ],
            "configuration": {
              "S3Bucket": "my-source-bucket",
              "S3ObjectKey": "source.zip"
            }
          }
        ]
      },
      {
        "name": "Build",
        "actions": [
          {
            "name": "BuildAction",
            "actionTypeId": {
              "category": "Build",
              "owner": "AWS",
              "provider": "CodeBuild",
              "version": "1"
            },
            "inputArtifacts": [
              {
                "name": "SourceArtifact"
              }
            ],
            "outputArtifacts": [
              {
                "name": "BuildArtifact"
              }
            ],
            "configuration": {
              "ProjectName": "MyCodeBuildProject"
            }
          }
        ]
      }
    ]
  }
}
```

---

## Bonnes pratiques

1. **Automatiser les tests** : Intégrez des tests unitaires, d'intégration, et fonctionnels dans vos pipelines.
2. **Utiliser des environnements isolés** : Exécutez les pipelines dans des environnements dédiés pour éviter les interférences.
3. **Surveiller les pipelines** : Configurez des alertes pour détecter les échecs rapidement.
4. **Sécuriser les secrets** : Stockez les clés API et autres secrets dans des gestionnaires sécurisés.
5. **Optimiser les étapes** : Minimisez les étapes inutiles pour réduire les temps d'exécution.
6. **Versionner les configurations** : Ajoutez les fichiers de configuration des pipelines au contrôle de version pour garantir la cohérence.
7. **Analyser les performances** : Utilisez des outils comme SonarQube pour surveiller la qualité du code et des pipelines.

---

## Outils utiles

- **Jenkins** : Automatisation des pipelines CI/CD.
- **GitLab CI/CD** : Intégré à GitLab pour gérer les pipelines.
- **GitHub Actions** : Workflows CI/CD dans les dépôts GitHub.
- **Azure DevOps** : Plateforme complète pour CI/CD et gestion de projet.
- **AWS CodePipeline** : Automatisation des étapes CI/CD sur AWS.
- **SonarQube** : Analyse de la qualité du code.
- **Postman** : Test des API dans les pipelines CI/CD.

---

## Liens utiles

- [Documentation Jenkins](https://www.jenkins.io/doc/)
- [Documentation GitLab CI/CD](https://docs.gitlab.com/ee/ci/)
- [Documentation GitHub Actions](https://docs.github.com/en/actions)
- [Documentation Azure DevOps](https://learn.microsoft.com/en-us/azure/devops/)
- [Documentation AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html)
- [Tutoriels CI/CD](https://www.tutorialspoint.com/ci_cd/index.htm)
