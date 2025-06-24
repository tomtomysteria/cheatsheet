# 📦 Kubernetes

## Introduction

Kubernetes est une plateforme open-source pour automatiser le déploiement, la mise à l'échelle et la gestion des conteneurs. Il est largement utilisé pour orchestrer des applications conteneurisées dans des environnements de production.

---

## Commandes essentielles

### Gestion des pods

```bash
kubectl get pods                     # Liste les pods en cours d'exécution
kubectl describe pod <pod-name>      # Affiche les détails d'un pod
kubectl logs <pod-name>              # Affiche les logs d'un pod
kubectl delete pod <pod-name>        # Supprime un pod
```

### Gestion des déploiements

```bash
kubectl apply -f deployment.yaml     # Applique un fichier de déploiement
kubectl get deployments              # Liste les déploiements
kubectl scale deployment <name> --replicas=3  # Met à l'échelle un déploiement
kubectl delete deployment <name>     # Supprime un déploiement
```

### Gestion des services

```bash
kubectl get services                 # Liste les services
kubectl describe service <service-name> # Affiche les détails d'un service
kubectl delete service <service-name> # Supprime un service
```

---

## Exemples pratiques

### Exemple de fichier `deployment.yaml`

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app-container
        image: nginx
        ports:
        - containerPort: 80
```

### Exemple de fichier `service.yaml`

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-app-service
spec:
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: LoadBalancer
```

### Déploiement et gestion

1. **Déployer une application** :

   ```bash
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   ```

2. **Vérifier les ressources** :

   ```bash
   kubectl get pods
   kubectl get services
   ```

3. **Mettre à l'échelle** :

   ```bash
   kubectl scale deployment my-app --replicas=5
   ```

---

## Bonnes pratiques

1. **Utiliser des namespaces** : Organisez vos ressources en namespaces pour une meilleure isolation.

   ```bash
   kubectl create namespace my-namespace
   kubectl apply -f deployment.yaml -n my-namespace
   ```

2. **Surveiller les ressources** : Utilisez `kubectl top` pour surveiller l'utilisation des ressources.

   ```bash
   kubectl top pods
   kubectl top nodes
   ```

3. **Automatiser les déploiements** : Intégrez Kubernetes dans vos pipelines CI/CD pour des déploiements automatisés.

---

## Liens utiles

- [Documentation officielle Kubernetes](https://kubernetes.io/docs/)
- [Tutoriels Kubernetes](https://kubernetes.io/docs/tutorials/)
- [Exemples de configuration Kubernetes](https://github.com/kubernetes/examples)
