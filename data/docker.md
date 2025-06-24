# 📦 Docker

## Introduction

Docker est une plateforme permettant de créer, déployer et exécuter des applications dans des conteneurs. Les conteneurs offrent une solution légère et portable pour exécuter des applications dans des environnements isolés.

---

## Commandes essentielles

### Gestion des conteneurs

```bash
docker ps                     # Liste les conteneurs en cours d'exécution
docker ps -a                  # Liste tous les conteneurs (actifs et arrêtés)
docker start <container-id>   # Démarre un conteneur arrêté
docker stop <container-id>    # Arrête un conteneur actif
docker rm <container-id>      # Supprime un conteneur
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
docker exec -it <container-id> bash # Accède au shell d'un conteneur
docker logs <container-id>        # Affiche les logs d'un conteneur
docker run -d my-app              # Exécute un conteneur en mode détaché
```

### Explication de l'option `-d`

L'option `-d` (détaché) permet d'exécuter un conteneur en arrière-plan. Cela signifie que le conteneur s'exécute sans bloquer le terminal, ce qui est utile pour les services ou applications qui doivent fonctionner en continu.

Exemple :

```bash
docker run -d -p 3000:3000 my-app
```

Dans cet exemple, le conteneur est exécuté en arrière-plan et les ports sont mappés.

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
```

---

## Bonnes pratiques

1. **Minimiser la taille des images** : Utilisez des images de base légères comme `alpine`.
2. **Nettoyer les conteneurs et images inutilisés** : Utilisez `docker system prune` pour libérer de l'espace.
3. **Utiliser des volumes** : Configurez des volumes pour persister les données entre les conteneurs.

---

## Liens utiles

- [Documentation officielle Docker](https://docs.docker.com)
- [Docker Hub](https://hub.docker.com)
- [Guide Docker Compose](https://docs.docker.com/compose/)
