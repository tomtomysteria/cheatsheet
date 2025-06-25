# 📦 Kubernetes

## Introduction

Kubernetes est une plateforme open-source pour orchestrer des applications conteneurisées. Il automatise le déploiement, la mise à l'échelle et la gestion des conteneurs dans des environnements de production. Kubernetes est conçu pour gérer des architectures complexes, garantir la haute disponibilité et simplifier la gestion des ressources.

---

## Exemple de pipeline CI/CD avec Docker et Kubernetes

Voici un exemple de pipeline CI/CD utilisant Docker pour construire des images et Kubernetes pour déployer des conteneurs. Ce pipeline est conçu pour GitLab CI/CD.

```yaml
stages:
  - build
  - test
  - deploy

variables:
  IMAGE_NAME: registry.example.com/my-app
  KUBECONFIG: $CI_PROJECT_DIR/kubeconfig

build:
  stage: build
  script:
    # Construire l'image Docker
    - docker build -t $IMAGE_NAME:$CI_COMMIT_SHA .
    # Pousser l'image vers le registre Docker
    - docker push $IMAGE_NAME:$CI_COMMIT_SHA

test:
  stage: test
  script:
    # Exécuter des tests dans un conteneur Docker
    - docker run --rm $IMAGE_NAME:$CI_COMMIT_SHA npm test

deploy:
  stage: deploy
  environment:
    name: production
    url: https://my-app.example.com
  script:
    # Configurer kubectl avec le fichier kubeconfig
    - export KUBECONFIG=$KUBECONFIG
    # Mettre à jour le déploiement Kubernetes avec la nouvelle image
    - kubectl set image deployment/my-app my-app-container=$IMAGE_NAME:$CI_COMMIT_SHA
    # Vérifier que le déploiement est en cours
    - kubectl rollout status deployment/my-app
```

### Explications

1. **Étape `build`** :
   - Construire une image Docker avec le code source.
   - Pousser l'image vers un registre Docker (exemple : Docker Hub ou un registre privé).

2. **Étape `test`** :
   - Exécuter des tests dans un conteneur Docker basé sur l'image construite.

3. **Étape `deploy`** :
   - Utiliser `kubectl` pour déployer l'image sur un cluster Kubernetes.
   - Mettre à jour le déploiement Kubernetes avec la nouvelle image.
   - Vérifier que le déploiement est terminé avec `kubectl rollout status`.

### Prérequis

- **Docker** : Installé sur l'environnement CI/CD pour construire et exécuter des conteneurs.
- **Kubernetes** : Un cluster configuré avec un fichier `kubeconfig` accessible dans le pipeline.
- **Registre Docker** : Un registre pour stocker les images Docker (exemple : Docker Hub, GitLab Container Registry).

---

## Kubernetes vs Docker Compose

### Parallèle avec Docker Compose

Docker Compose est un outil utilisé pour orchestrer des conteneurs dans un environnement local. Il est idéal pour les environnements de développement ou les petites applications. Kubernetes, en revanche, est conçu pour orchestrer des conteneurs à grande échelle dans des environnements de production. Voici les principales différences :

1. **Portée** :
   - Docker Compose est limité à un environnement local ou à un seul hôte.
   - Kubernetes est conçu pour fonctionner sur plusieurs nœuds et dans des environnements distribués.

2. **Scalabilité** :
   - Docker Compose permet de gérer des conteneurs, mais il n'offre pas de mécanismes avancés de mise à l'échelle.
   - Kubernetes offre des fonctionnalités de mise à l'échelle automatique basées sur la charge.

3. **Haute disponibilité** :
   - Docker Compose ne garantit pas la haute disponibilité.
   - Kubernetes garantit que les pods sont redémarrés en cas de panne et offre des mécanismes de réplication.

4. **Gestion des ressources** :
   - Docker Compose ne permet pas de définir des limites de ressources (CPU, mémoire).
   - Kubernetes permet de configurer des limites et des demandes de ressources pour chaque pod.

### Kubernetes et Docker

Kubernetes peut utiliser Docker comme runtime pour exécuter les conteneurs. Docker est l'un des moteurs de conteneurs pris en charge par Kubernetes, bien que d'autres moteurs comme containerd ou CRI-O soient également compatibles. Voici comment Kubernetes et Docker interagissent :

1. **Docker comme runtime** :
   - Kubernetes utilise Docker pour créer, exécuter et gérer les conteneurs au sein des pods.
   - Docker fournit les outils nécessaires pour construire des images conteneurisées qui sont ensuite déployées par Kubernetes.

2. **Interopérabilité** :
   - Les images Docker peuvent être directement utilisées dans Kubernetes sans modification.
   - Kubernetes peut orchestrer des conteneurs Docker sur plusieurs nœuds, offrant une gestion avancée des ressources et une scalabilité.

3. **Transition vers containerd** :
   - Depuis Kubernetes 1.20, Docker n'est plus le runtime par défaut. Kubernetes utilise désormais containerd comme runtime principal, bien que Docker reste compatible.

### Utilisation de Kubernetes en local

Kubernetes peut être utilisé en local grâce à des outils comme **Minikube** ou **Kind** (Kubernetes in Docker). Ces outils permettent de simuler un cluster Kubernetes sur une machine locale, ce qui est utile pour :

1. **Tester les configurations Kubernetes** avant de les déployer en production.
2. **Simuler des environnements complexes** avec plusieurs pods, services, et namespaces.
3. **Apprendre Kubernetes** sans avoir besoin d'un cluster distant.

#### Exemple avec Minikube

1. **Installer Minikube** :

   ```bash
   curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
   sudo install minikube-linux-amd64 /usr/local/bin/minikube
   ```

2. **Démarrer un cluster local** :

   ```bash
   minikube start
   ```

3. **Utiliser kubectl avec Minikube** :

   ```bash
   kubectl get pods
   ```

### Intérêt par rapport à Docker Compose

Bien que Docker Compose soit plus simple à utiliser pour des projets locaux ou de petite taille, Kubernetes offre des avantages significatifs pour les projets nécessitant :

- **Scalabilité** : Kubernetes peut gérer des milliers de conteneurs répartis sur plusieurs nœuds.
- **Gestion avancée des ressources** : Kubernetes permet de définir des limites de CPU et de mémoire pour chaque pod.
- **Automatisation** : Kubernetes automatise la mise à l'échelle, le redémarrage des conteneurs, et la gestion des défaillances.
- **Interopérabilité** : Les configurations Kubernetes sont portables et peuvent être utilisées dans des environnements cloud ou hybrides.

---

## Concepts clés

### Pod

Un pod est l'unité de base de Kubernetes. Il représente un ou plusieurs conteneurs qui partagent le même réseau et le même stockage.

### Déploiement

Un déploiement gère la création et la mise à jour des pods. Il garantit que le nombre de réplicas spécifié est toujours en cours d'exécution.

### Service

Un service expose les pods à l'extérieur ou à d'autres ressources internes. Il permet de gérer la communication entre les composants.

### Namespace

Les namespaces permettent d'isoler les ressources Kubernetes dans des environnements logiques distincts.

---

## Commandes essentielles

### Gestion des pods

```bash
kubectl get pods                     # Liste les pods en cours d'exécution
kubectl describe pod <pod-name>      # Affiche les détails d'un pod
kubectl logs <pod-name>              # Affiche les logs d'un pod
kubectl delete pod <pod-name>        # Supprime un pod
kubectl exec -it <pod-name> -- bash  # Accède au shell d'un pod
```

### Gestion des déploiements

```bash
kubectl apply -f deployment.yaml     # Applique un fichier de déploiement
kubectl get deployments              # Liste les déploiements
kubectl describe deployment <name>   # Affiche les détails d'un déploiement
kubectl scale deployment <name> --replicas=3  # Met à l'échelle un déploiement
kubectl delete deployment <name>     # Supprime un déploiement
```

### Gestion des services

```bash
kubectl get services                 # Liste les services
kubectl describe service <service-name> # Affiche les détails d'un service
kubectl delete service <service-name> # Supprime un service
```

### Gestion des namespaces

```bash
kubectl get namespaces               # Liste les namespaces
kubectl create namespace <name>      # Crée un namespace
kubectl delete namespace <name>      # Supprime un namespace
kubectl apply -f resource.yaml -n <namespace> # Applique une ressource dans un namespace
```

### Surveillance des ressources

```bash
kubectl top pods                     # Affiche l'utilisation des ressources des pods
kubectl top nodes                    # Affiche l'utilisation des ressources des nœuds
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

4. **Configurer les limites de ressources** : Ajoutez des limites de CPU et de mémoire pour éviter les surcharges.

   ```yaml
   resources:
     limits:
       memory: "512Mi"
       cpu: "500m"
   ```

5. **Utiliser des labels** : Ajoutez des labels aux ressources pour simplifier leur gestion et leur sélection.

---

## Enjeux du développement avec Kubernetes

1. **Scalabilité** : Kubernetes permet de mettre à l'échelle les applications en fonction de la charge.
2. **Haute disponibilité** : Kubernetes garantit que les applications restent disponibles même en cas de panne.
3. **Portabilité** : Les configurations Kubernetes fonctionnent sur différents environnements (local, cloud, hybride).
4. **Complexité** : Bien que puissant, Kubernetes nécessite une courbe d'apprentissage pour maîtriser ses concepts.
5. **Sécurité** : Implémentez des politiques RBAC (Role-Based Access Control) pour sécuriser l'accès aux ressources.

---

## Liens utiles

- [Documentation officielle Kubernetes](https://kubernetes.io/docs/)
- [Tutoriels Kubernetes](https://kubernetes.io/docs/tutorials/)
- [Exemples de configuration Kubernetes](https://github.com/kubernetes/examples)
- [Kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
