# 📦 Jenkins

## Introduction

Jenkins est un serveur d’automatisation CI/CD. Il orchestre des builds, tests et déploiements via des **jobs** et surtout via des **pipelines** définis dans un `Jenkinsfile` (Pipeline as Code).

Points clés :

- Très flexible (plugins)
- S’intègre bien avec Maven/Gradle, Docker, Kubernetes
- Requiert une gouvernance (plugins, credentials, agents)

---

## Concepts clés

### Controller / agents

- **controller** : interface + orchestration.
- **agent** : exécute réellement les étapes (`sh`, `mvn`, `npm`, …).

### Pipeline as Code (Jenkinsfile)

Deux styles :

- **Declarative Pipeline** (le plus courant)
- **Scripted Pipeline** (plus libre, plus complexe)

### Credentials

Jenkins stocke les secrets dans un store (credentials). On les injecte au runtime (éviter les secrets en clair).

---

## Jenkinsfile (Declarative) – Exemple Java Maven

```groovy
pipeline {
  agent any

  options {
    timestamps()
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build') {
      steps {
        sh 'mvn -B -DskipTests package'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn -B test'
      }
      post {
        always {
          junit 'target/surefire-reports/TEST-*.xml'
        }
      }
    }
  }
}
```

---

## Jenkinsfile – Exemple Angular

```groovy
pipeline {
  agent any

  stages {
    stage('Install') {
      steps {
        sh 'npm ci'
      }
    }

    stage('Test') {
      steps {
        sh 'npm test -- --watch=false'
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build'
      }
      post {
        success {
          archiveArtifacts artifacts: 'dist/**', fingerprint: true
        }
      }
    }
  }
}
```

---

## Intégration Docker

```groovy
pipeline {
  agent any

  stages {
    stage('Build image') {
      steps {
        sh 'docker build -t my-app:${GIT_COMMIT} .'
      }
    }

    stage('Push image') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker-registry', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
          sh 'echo "$PASS" | docker login -u "$USER" --password-stdin registry.example.com'
          sh 'docker tag my-app:${GIT_COMMIT} registry.example.com/my-app:${GIT_COMMIT}'
          sh 'docker push registry.example.com/my-app:${GIT_COMMIT}'
        }
      }
    }
  }
}
```

---

## Bonnes pratiques

1. **Pipeline as Code** : versionner le `Jenkinsfile`.
2. **Agents dédiés** : éviter d’exécuter les builds sur le controller.
3. **Nettoyage** : nettoyer workspace, images Docker, caches.
4. **Credentials** : toujours via `withCredentials`.
5. **Plugins** : limiter et mettre à jour régulièrement.

---

## Liens utiles

- Jenkins Pipeline : https://www.jenkins.io/doc/book/pipeline/
- Declarative Pipeline syntax : https://www.jenkins.io/doc/book/pipeline/syntax/
