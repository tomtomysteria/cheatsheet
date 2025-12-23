# 📦 Helm

## Introduction

Helm est le **package manager** de Kubernetes. Il permet de déployer des applications via des **charts** (templates Kubernetes paramétrables) et de gérer des **releases** (versions déployées).

Pourquoi Helm :

- Paramétrage via `values.yaml`
- Réutilisation (chart repo)
- Upgrade / rollback simples

---

## Concepts clés

### Chart

Un chart contient :

- `Chart.yaml` : metadata
- `values.yaml` : valeurs par défaut
- `templates/` : manifestes Kubernetes templatisés

### Release

Une release = une instance installée d’un chart, avec un nom (ex: `my-app-prod`).

---

## Commandes essentielles

```bash
helm version
helm repo add <name> <url>
helm repo update

helm create my-chart
helm lint ./my-chart

helm install my-app ./my-chart -n my-namespace --create-namespace
helm upgrade my-app ./my-chart -n my-namespace
helm upgrade --install my-app ./my-chart -n my-namespace

helm list -n my-namespace
helm status my-app -n my-namespace
helm history my-app -n my-namespace
helm rollback my-app 3 -n my-namespace

helm uninstall my-app -n my-namespace
```

### Rendu des templates (debug)

```bash
helm template my-app ./my-chart -n my-namespace -f values.yaml
```

### Override de valeurs sans fichier

Pratique en CI/CD :

```bash
helm upgrade --install my-app ./my-chart -n my-namespace --create-namespace \
  --set image.repository=$CI_REGISTRY_IMAGE \
  --set image.tag=$CI_COMMIT_SHA
```

Avec un fichier de valeurs par environnement :

```bash
helm upgrade --install my-app ./my-chart -n my-namespace --create-namespace \
  -f values-prod.yaml \
  --set image.tag=$CI_COMMIT_SHA
```

---

## Exemple de `values.yaml` (app Spring Boot)

```yaml
image:
  repository: registry.example.com/my-app
  tag: "1.0.0"

service:
  type: ClusterIP
  port: 8080

env:
  SPRING_PROFILES_ACTIVE: prod

resources:
  requests:
    cpu: "100m"
    memory: "256Mi"
  limits:
    cpu: "500m"
    memory: "512Mi"
```

---

## Helm vs kubectl apply

- `kubectl apply` : tu appliques des YAML “statics”.
- Helm : tu installe une release, tu upgrades, tu rollback, tu gères des valeurs.

---

## Bonnes pratiques

1. **Séparer values par environnement** : `values-dev.yaml`, `values-prod.yaml`.
2. **Versionner les charts** (`Chart.yaml`) et tagger les images.
3. **Templates simples** : éviter la logique complexe dans Helm.
4. **Rollback** : utiliser `helm history` + `helm rollback`.
5. **Secrets** : gérer via Secret manager (ou SealedSecrets/ExternalSecrets), éviter secrets en clair.

---

## Liens utiles

- [Helm](https://helm.sh/docs/)
- [Best practices](https://helm.sh/docs/chart_best_practices/)
