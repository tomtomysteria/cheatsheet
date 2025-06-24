# 📦 CI/CD

## Introduction

CI/CD (Intégration Continue / Déploiement Continu) est une pratique essentielle pour automatiser les tests, les intégrations et les déploiements. Elle permet de réduire les erreurs humaines et d'accélérer les cycles de développement.

---

## Commandes essentielles

### GitLab CI/CD

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

### Azure DevOps

```yaml
trigger:
  - main

pool:
  vmImage: 'ubuntu-latest'

steps:
  - script: npm install
  - script: npm run build
  - script: npm test
```

### Jenkins Pipeline

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

## Bonnes pratiques

1. **Automatisation complète** : Automatisez les tests, les builds et les déploiements pour éviter les erreurs humaines.
2. **Utilisation de branches** : Utilisez des branches dédiées pour les tests et les déploiements.
3. **Monitoring** : Configurez des outils de monitoring pour surveiller les pipelines CI/CD.

---

## Liens utiles

- [Documentation GitLab CI/CD](https://docs.gitlab.com/ee/ci/)
- [Documentation Azure DevOps](https://learn.microsoft.com/en-us/azure/devops/pipelines/)
- [Documentation Jenkins](https://www.jenkins.io/doc/book/pipeline/)
