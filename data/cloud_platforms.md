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

### Enjeux pour les développeurs

1. **Gestion des coûts** : Surveillez l'utilisation des ressources pour éviter les dépenses inutiles.
2. **Sécurisation des données** : Implémentez des politiques strictes pour protéger les données sensibles.
3. **Automatisation** : Utilisez des outils comme Terraform ou CloudFormation pour gérer l'infrastructure.
4. **Interopérabilité** : Assurez-vous que les services cloud sont compatibles avec les outils et frameworks utilisés.

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

## Services clés

### AWS

- **S3** : Stockage d'objets.
- **EC2** : Machines virtuelles.
- **Lambda** : Fonctions serverless.
- **RDS** : Bases de données relationnelles.
- **CloudFormation** : Infrastructure as Code.
- **ECS** : Orchestration de conteneurs.
- **ECR** : Registre de conteneurs.

### Azure

- **Azure Blob Storage** : Stockage d'objets.
- **Azure Virtual Machines** : Machines virtuelles.
- **Azure Functions** : Fonctions serverless.
- **Azure SQL Database** : Bases de données relationnelles.
- **Azure Kubernetes Service (AKS)** : Orchestration de conteneurs.
- **Azure Container Registry (ACR)** : Registre de conteneurs.

### GCP

- **Google Cloud Storage** : Stockage d'objets.
- **Compute Engine** : Machines virtuelles.
- **Cloud Functions** : Fonctions serverless.
- **Cloud SQL** : Bases de données relationnelles.
- **BigQuery** : Analyse de données.
- **Google Kubernetes Engine (GKE)** : Orchestration de conteneurs.

---

## Bonnes pratiques

1. **Automatiser les déploiements** : Utilisez des outils comme Terraform ou CloudFormation pour gérer l'infrastructure.
2. **Surveiller les ressources** : Configurez des alertes et des tableaux de bord pour suivre les performances.
3. **Sécuriser les accès** : Implémentez des politiques IAM strictes pour protéger les ressources.
4. **Optimiser les coûts** : Surveillez l'utilisation des ressources et supprimez celles inutilisées.
5. **Utiliser des environnements isolés** : Créez des environnements distincts pour le développement, les tests, et la production.
6. **Configurer les sauvegardes** : Automatisez les sauvegardes pour garantir la récupération des données en cas de panne.
7. **Analyser les performances** : Utilisez des outils comme AWS CloudWatch, Azure Monitor, ou GCP Stackdriver.

---

## Outils utiles

- **Terraform** : Infrastructure as Code pour gérer les ressources cloud.
- **CloudFormation** : Gestion de l'infrastructure AWS.
- **Azure Resource Manager (ARM)** : Gestion des ressources Azure.
- **Google Deployment Manager** : Gestion des ressources GCP.
- **Postman** : Test des API cloud.
- **SonarQube** : Analyse de la qualité du code.
- **Prometheus/Grafana** : Surveillance des performances des applications.

---

## Liens utiles

- [Documentation AWS](https://aws.amazon.com/documentation/)
- [Documentation Azure](https://learn.microsoft.com/en-us/azure/)
- [Documentation GCP](https://cloud.google.com/docs)
- [Documentation GitLab](https://docs.gitlab.com/ee/ci/)
- [Tutoriels Cloud Platforms](https://www.tutorialspoint.com/cloud_computing/index.htm)
