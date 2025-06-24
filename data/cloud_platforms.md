# 📦 Cloud Platforms (AWS, GCP, Azure, GitLab)

## Introduction

Les plateformes cloud permettent de déployer, gérer et mettre à l'échelle des applications à grande échelle. Elles offrent des outils pour le stockage, le calcul, et les bases de données.

---

## Commandes essentielles

### AWS CLI

```bash
aws configure                # Configure les identifiants AWS
aws s3 ls                    # Liste les buckets S3
aws ec2 describe-instances   # Liste les instances EC2
aws dynamodb list-tables     # Liste les tables DynamoDB
```

### GCP CLI

```bash
gcloud init                  # Initialise la configuration GCP
gcloud compute instances list # Liste les instances Compute Engine
gcloud storage buckets list  # Liste les buckets de stockage
gcloud functions deploy      # Déploie une fonction cloud
```

### Azure CLI

```bash
az login                     # Connecte à Azure
az group list                # Liste les groupes de ressources
az vm list                   # Liste les machines virtuelles
az storage blob list         # Liste les blobs de stockage
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

## Bonnes pratiques

1. **Automatisation** : Utilisez des scripts pour automatiser les tâches répétitives.
2. **Monitoring** : Configurez des outils de surveillance pour suivre les performances et les erreurs.
3. **Sécurité** : Implémentez des politiques de sécurité strictes pour protéger les données et les ressources.

---

## Liens utiles

- [AWS Documentation](https://aws.amazon.com/documentation/)
- [GCP Documentation](https://cloud.google.com/docs)
- [Azure Documentation](https://learn.microsoft.com/en-us/azure/)
- [GitLab Documentation](https://docs.gitlab.com/ee/ci/)
