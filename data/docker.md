# 📦 Docker

## Introduction

Docker est une plateforme permettant de créer, déployer et exécuter des applications dans des conteneurs. Les conteneurs offrent une solution légère, portable et isolée pour exécuter des applications dans des environnements homogènes. Docker est largement utilisé pour le développement, les tests, et la mise en production des applications modernes.

---

## Usages principaux de Docker

Docker a deux usages principaux :

1. **Création et gestion d'images (Build/Push)** :
   Docker est l'outil standard pour créer des images de conteneurs qui sont ensuite :
   - Testées localement.
   - Stockées dans un registre (Docker Hub, GitLab, ECR, etc.).
   - Déployées dans des environnements cloud via des outils comme Kubernetes.

   ✅ Docker est essentiel dans les pipelines CI/CD :
   - Pour builder, tester, scanner, puis publier une image.

2. **Exécution de conteneurs (Runtime)** :
   Docker peut exécuter des conteneurs en local ou sur une VM unique.
   - Pour des besoins simples, vous pouvez lancer un conteneur avec `docker run`, ou un ensemble avec `docker-compose up`.
   - ❗ Cependant, dans des environnements de production à grande échelle, on évite d'utiliser Docker directement comme runtime. On préfère Kubernetes ou un orchestrateur (qui peut utiliser containerd au lieu de Docker depuis 2020).

---

## Résumé des usages

| Usage                          | Utilisation                                                                 |
|--------------------------------|-----------------------------------------------------------------------------|
| 🏗️ **Construire des images**   | Dans les pipelines CI/CD, pour créer l'image de l'application.              |
| 📦 **Exécuter des conteneurs** | Pour du développement, des tests, ou des petits déploiements.               |
| 🔧 **Runtime d'orchestration** | Moins courant en production moderne (remplacé par Kubernetes + containerd). |

---

## Concepts clés

### Conteneurs et images

- **Image** : Une image Docker est un modèle immuable contenant tout ce dont une application a besoin pour fonctionner (code, dépendances, configuration).
- **Conteneur** : Un conteneur est une instance d'une image en cours d'exécution. Il est isolé et peut être démarré, arrêté ou supprimé.

### Dockerfile

Un Dockerfile est un fichier texte contenant les instructions pour construire une image Docker.

```dockerfile
# Exemple de Dockerfile
FROM node:16
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
CMD ["npm", "start"]
EXPOSE 3000
```

### Volumes

Les volumes permettent de persister les données entre les redémarrages des conteneurs.

```bash
docker volume create <volume-name>   # Créer un volume
docker volume ls                     # Lister les volumes
docker volume rm <volume-name>       # Supprimer un volume
```

### Réseaux

Docker permet de créer des réseaux pour connecter plusieurs conteneurs.

```bash
docker network create <network-name> # Créer un réseau Docker
docker network ls                    # Lister les réseaux disponibles
docker network connect <network-name> <container-id> # Connecter un conteneur à un réseau
```

---

## Commandes essentielles

### Gestion des conteneurs

```bash
docker ps                     # Liste les conteneurs en cours d'exécution
docker ps -a                  # Liste tous les conteneurs (actifs et arrêtés)
docker start <container-id>   # Démarre un conteneur arrêté
docker stop <container-id>    # Arrête un conteneur actif
docker rm <container-id>      # Supprime un conteneur
docker logs <container-id>    # Affiche les logs d'un conteneur
docker exec -it <container-id> bash # Accède au shell d'un conteneur
```

### Gestion des images

```bash
docker images                 # Liste les images locales
docker pull <image-name>      # Télécharge une image depuis Docker Hub
docker rmi <image-id>         # Supprime une image locale
docker build -t my-app .      # Crée une image à partir d'un Dockerfile
```

### Exécution des conteneurs

```bash
docker run -p 3000:3000 my-app    # Exécute un conteneur et mappe les ports
docker run -d my-app              # Exécute un conteneur en mode détaché
docker run --name <container-name> my-app # Exécute un conteneur avec un nom spécifique
```

### Nettoyage des ressources

```bash
docker system prune               # Supprime les conteneurs, images et volumes inutilisés
docker system prune -a            # Supprime aussi les images non utilisées (pas seulement les dangling)
docker system prune -a -f         # Idem sans demander de confirmation (force)
docker volume prune               # Supprime les volumes inutilisés
docker network prune              # Supprime les réseaux inutilisés
```

---

## Docker Compose - Commandes avancées

### 🚀 1️⃣ Gestion des conteneurs (démarrer / arrêter / redémarrer)

```bash
docker-compose up -d              # Démarre les services définis dans docker-compose.yaml en arrière-plan
docker-compose up -d --build      # Rebuild les images avant de démarrer les conteneurs
docker-compose down               # Arrête et supprime les conteneurs (garde les volumes)
docker-compose down -v            # Arrête et supprime les conteneurs et les volumes (reset base de données, etc.)
docker-compose down && docker-compose up -d --build # Redémarre tout en reconstruisant les images
docker-compose restart <service>  # Redémarre un service spécifique
docker-compose ps                 # Affiche l'état des conteneurs du projet courant
docker-compose -f <path> ps       # Affiche l'état des conteneurs pour un autre fichier docker-compose
```

#### 🎯 En pratique (cas concrets)

**✅ Tu as fini ta journée**
→ `stop` suffit largement.

**✅ Tu veux repartir vite demain**
→ `stop` + `start`

**✅ Tu as modifié la config réseau / variables d'environnement**
→ `down` puis `up`

**✅ Docker fait des trucs bizarres**
→ `down` (voire `down -v` si gros reset)

**🧠 Résumé ultra simple**

| Commande | Action               |
|----------|----------------------|
| `stop`   | pause                |
| `down`   | suppression          |
| `start`  | reprendre            |
| `up`     | créer + démarrer     |

### 🔍 2️⃣ Consultation des logs

```bash
docker-compose logs               # Affiche les logs des services
docker-compose logs -f            # Suit les logs en temps réel (mode "tail -f")
docker-compose logs --tail=N      # Affiche seulement les N dernières lignes
docker-compose logs <service>     # Affiche les logs d'un service précis
docker-compose logs --no-log-prefix # Supprime le préfixe du nom du service dans les logs
```

### 🖥 3️⃣ Accéder à un conteneur

```bash
docker exec -it <container> bash  # Ouvre un terminal bash dans un conteneur en cours d'exécution
docker exec -it <container> sh    # Ouvre un shell sh (si bash non disponible)
docker exec -it <container> ls -la # Exécute une commande spécifique dans un conteneur
docker-compose exec <service> <commande> # Exécute une commande dans un conteneur déjà démarré
docker-compose exec -T <service> <commande> # Même chose mais sans pseudo-TTY (utile pour scripts CI/CD)
```

### 🧪 4️⃣ Debug / Inspection

```bash
docker-compose run --rm --entrypoint env <service> # Lance temporairement un conteneur et affiche les variables d'environnement
docker run --rm --env-file .env <image> python debug_env.py # Lance une image Docker avec un fichier .env et exécute un script Python
```

---

## Exemples pratiques

### Exemple de Dockerfile

Créez un fichier `Dockerfile` pour construire une image personnalisée.

```dockerfile
FROM node:16
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
CMD ["npm", "start"]
EXPOSE 3000
```

### Construire et exécuter une image

```bash
docker build -t my-app .
docker run -p 3000:3000 my-app
```

### Utilisation de Docker Compose

Créez un fichier `docker-compose.yml` pour orchestrer plusieurs conteneurs.

```yaml
version: '3'
services:
  web:
    image: my-app
    ports:
      - "3000:3000"
  db:
    image: postgres
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
```

Exécutez les services avec :

```bash
docker-compose up -d
docker-compose down               # Arrête et supprime les conteneurs
```

---

## Bonnes pratiques

## À connaître en entreprise (Dockerfile)

### Multi-stage build (exemple Spring Boot)

Objectif : image runtime plus petite.

```dockerfile
FROM maven:3.9.9-eclipse-temurin-21 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn -B -DskipTests package

FROM eclipse-temurin:21-jre
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
```

### Points clés

- `.dockerignore` (accélère et évite d’embarquer des secrets)
- tags immuables (SHA) en CI
- utilisateur non-root si possible

1. **Minimiser la taille des images** : Utilisez des images de base légères comme `alpine`.
2. **Nettoyer les conteneurs et images inutilisés** : Utilisez `docker system prune` pour libérer de l'espace.
3. **Utiliser des volumes** : Configurez des volumes pour persister les données entre les conteneurs.
4. **Automatiser les builds** : Intégrez Docker dans vos pipelines CI/CD pour automatiser la construction et le déploiement des conteneurs.
5. **Isoler les services** : Utilisez un conteneur par service pour simplifier la gestion et la scalabilité.
6. **Sécuriser les conteneurs** : Limitez les permissions des conteneurs et utilisez des images vérifiées.

---

## Enjeux du développement avec Docker

1. **Portabilité** : Les conteneurs Docker fonctionnent de manière identique sur différents environnements (local, cloud, etc.).
2. **Isolation** : Les conteneurs isolent les applications et leurs dépendances, réduisant les conflits.
3. **Scalabilité** : Docker facilite la mise à l'échelle des applications grâce à des orchestrateurs comme Kubernetes.
4. **Sécurité** : Bien que Docker offre une isolation, il est essentiel de sécuriser les images et les configurations.
5. **Performance** : Les conteneurs sont légers et démarrent rapidement, mais leur performance dépend de la configuration de l'hôte.

---

## Liens utiles

- [Documentation officielle Docker](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Guide Docker Compose](https://docs.docker.com/compose/)
- [Exemples de projets Docker](https://github.com/docker/docker)
