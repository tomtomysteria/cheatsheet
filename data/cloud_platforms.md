# 📦 Cloud Platforms (AWS, GCP, Azure, GitLab)

## Introduction

Les plateformes cloud permettent de déployer, gérer et mettre à l'échelle des applications à grande échelle. Elles offrent des outils pour le stockage, le calcul, les bases de données, et bien plus encore. Ces plateformes sont essentielles pour les développeurs modernes qui cherchent à construire des applications scalables, sécurisées, et performantes.

---

## Concepts clés

### Pourquoi utiliser les plateformes cloud ?

1. **Scalabilité** : Les ressources peuvent être ajustées dynamiquement en fonction des besoins.
2. **Flexibilité** : Les plateformes cloud prennent en charge une variété de services (calcul, stockage, bases de données, IA).
3. **Sécurité** : Les fournisseurs cloud offrent des outils avancés pour protéger les données et les applications.
4. **Coût optimisé** : Payez uniquement pour les ressources utilisées grâce aux modèles de tarification à la demande.

### Enjeux et Bonnes Pratiques pour les Développeurs

1. **Gestion des coûts** : Surveillez l'utilisation des ressources pour éviter les dépenses inutiles et optimisez les coûts en supprimant les ressources inutilisées.
2. **Sécurisation des données et des accès** : Implémentez des politiques strictes pour protéger les données sensibles et configurez des politiques IAM robustes.
3. **Automatisation** : Utilisez des outils comme Terraform, CloudFormation ou Kubernetes pour gérer l'infrastructure et orchestrer les ressources sur plusieurs plateformes.
4. **Surveillance des ressources** : Configurez des alertes et des tableaux de bord pour suivre les performances avec des outils comme Prometheus, Grafana, AWS CloudWatch, Azure Monitor, ou GCP Stackdriver.
5. **Interopérabilité et flexibilité** : Assurez-vous que les services cloud sont compatibles avec les outils et frameworks utilisés.
6. **Environnements isolés** : Créez des environnements distincts pour le développement, les tests, et la production.
7. **Sauvegardes et récupération** : Automatisez les sauvegardes pour garantir la récupération des données en cas de panne.
8. **Exemples pratiques** : Ajoutez des scripts Terraform ou CloudFormation pour automatiser les déploiements.

---

## Commandes essentielles

### AWS CLI

```bash
aws configure                # Configure les identifiants AWS
aws s3 ls                    # Liste les buckets S3
aws ec2 describe-instances   # Liste les instances EC2
aws dynamodb list-tables     # Liste les tables DynamoDB
aws lambda list-functions    # Liste les fonctions Lambda
aws cloudformation list-stacks # Liste les stacks CloudFormation
aws ecr get-login-password   # Récupère le mot de passe pour le registre ECR
aws ecs list-clusters        # Liste les clusters ECS
```

### GCP CLI

```bash
gcloud init                  # Initialise la configuration GCP
gcloud compute instances list # Liste les instances Compute Engine
gcloud storage buckets list  # Liste les buckets de stockage
gcloud functions deploy      # Déploie une fonction cloud
gcloud sql instances list    # Liste les instances Cloud SQL
gcloud container clusters list # Liste les clusters Kubernetes
```

### Azure CLI

```bash
az login                     # Connecte à Azure
az group list                # Liste les groupes de ressources
az vm list                   # Liste les machines virtuelles
az storage blob list         # Liste les blobs de stockage
az functionapp list          # Liste les applications Azure Functions
az aks list                  # Liste les clusters Kubernetes
az acr list                  # Liste les registres de conteneurs Azure
```

### GitLab CI/CD

```yaml
image: node:16

stages:
  - build
  - test
  - security
  - deploy
  - cleanup

variables:
  NODE_ENV: production
  API_KEY: $API_KEY

build:
  stage: build
  script:
    - echo "Installation des dépendances..."
    - npm install
    - echo "Construction de l'application..."
    - npm run build
  artifacts:
    paths:
      - dist/

test:
  stage: test
  script:
    - echo "Exécution des tests..."
    - npm test
  coverage: '/All files[^|]*\|[^|]*\s+([0-9]{1,3})%/'

security:
  stage: security
  script:
    - echo "Analyse de sécurité..."
    - npm audit || echo "Audit terminé avec des avertissements."
    - sonar-scanner || echo "Analyse SonarQube terminée."

deploy:
  stage: deploy
  script:
    - echo "Déploiement en cours..."
    - npm run deploy
  environment:
    name: production
    url: https://example.com
  only:
    - main
  after_script:
    - echo "Pipeline terminé. Envoi de notifications..."
    - curl -X POST -H "Content-Type: application/json" -d '{"text":"Pipeline terminé avec succès."}' https://hooks.slack.com/services/T00000000/B00000000/XXXXXXXXXXXXXXXXXXXXXXXX

cleanup:
  stage: cleanup
  script:
    - echo "Nettoyage des artefacts..."
    - rm -rf dist/
    - echo "Artefacts nettoyés."
```

---

## Services et Outils Cloud

### Stockage

- **AWS S3** : Stockage d'objets pour sauvegarder et partager des fichiers. Utilisé pour héberger des sites web statiques ou sauvegarder des fichiers volumineux.
- **Azure Blob Storage** : Stockage d'objets pour sauvegarder des fichiers volumineux.
- **Google Cloud Storage** : Stockage d'objets pour sauvegarder et partager des fichiers.

### Machines Virtuelles

- **AWS EC2** : Machines virtuelles pour exécuter des applications.
- **Azure Virtual Machines** : Machines virtuelles pour exécuter des applications.
- **Google Compute Engine** : Machines virtuelles pour exécuter des applications.

### Serverless

- **AWS Lambda** : Fonctions serverless pour exécuter du code sans gérer de serveurs. Exemple : Créez une API serverless pour gérer les requêtes HTTP.
- **Azure Functions** : Fonctions serverless pour exécuter du code sans infrastructure. Exemple : Traitez des événements en temps réel, comme les notifications.
- **Google Cloud Functions** : Fonctions serverless pour exécuter du code sans infrastructure. Exemple : Automatisez des tâches comme le traitement d'images.

### Bases de Données

- **AWS RDS** : Bases de données relationnelles entièrement gérées.
- **Azure SQL Database** : Bases de données relationnelles entièrement gérées.
- **Google Cloud SQL** : Bases de données relationnelles entièrement gérées.
- **Google BigQuery** : Analyse de données pour des requêtes massives.

### Orchestration et Conteneurs

- **AWS ECS** : Orchestration de conteneurs pour exécuter des applications conteneurisées.
- **Azure Kubernetes Service (AKS)** : Service géré par Azure basé sur Kubernetes, simplifiant la gestion des clusters Kubernetes.
- **Google Kubernetes Engine (GKE)** : Service géré par Google Cloud basé sur Kubernetes, offrant une gestion simplifiée des clusters.
- **Kubernetes** : Plateforme open-source d'orchestration de conteneurs. Peut être déployée sur des infrastructures locales, cloud non gérées, ou hybrides, offrant un contrôle total sur la configuration et la gestion des clusters.

### CI/CD

- **GitLab CI/CD** : Plateforme permettant de créer des pipelines d'intégration et de déploiement continus.
- **Jenkins** : Outil open-source très flexible pour automatiser les tâches CI/CD.
- **GitHub Actions** : Solution intégrée à GitHub pour automatiser les workflows CI/CD.
- **CircleCI** : Plateforme cloud optimisée pour les projets modernes.
- **Azure DevOps** : Suite complète pour CI/CD, gestion de projets, et collaboration.
- **Travis CI** : Plateforme CI/CD populaire pour les projets open-source.
- **Bitbucket Pipelines** : Solution CI/CD intégrée à Bitbucket.
- **TeamCity** : Plateforme CI/CD développée par JetBrains.

### Infrastructure as Code (IaC)

- **AWS CloudFormation** : Infrastructure as Code pour automatiser le déploiement des ressources.
- **Azure Resource Manager (ARM)** : Service Azure permettant de gérer les ressources cloud via des modèles JSON.
- **Google Deployment Manager** : Solution GCP pour déployer et gérer des ressources cloud.
- **Terraform** : Outil permettant de définir et de provisionner l'infrastructure cloud via des fichiers de configuration déclaratifs.

### Surveillance et Monitoring

- **AWS CloudWatch** : Service AWS pour surveiller les ressources et applications.
- **Azure Monitor** : Solution Azure pour surveiller les performances des ressources et applications.
- **GCP Stackdriver** : Plateforme GCP pour surveiller les ressources cloud et applications.
- **Prometheus/Grafana** : Ensemble d'outils pour surveiller les performances des applications.

### Tests et Qualité

- **Postman** : Outil pour tester les API.
- **SonarQube** : Plateforme d'analyse de la qualité du code.

---

## Liens utiles

- [Documentation AWS](https://aws.amazon.com/documentation/)
- [Documentation Azure](https://learn.microsoft.com/en-us/azure/)
- [Documentation GCP](https://cloud.google.com/docs)
- [Documentation GitLab](https://docs.gitlab.com/ee/ci/)
- [Tutoriels Cloud Platforms](https://www.tutorialspoint.com/cloud_computing/index.htm)
