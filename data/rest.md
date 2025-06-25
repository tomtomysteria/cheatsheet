# 📦 REST

## Introduction

REST (Representational State Transfer) est une architecture pour les API web qui repose sur les principes HTTP. Elle permet de créer des services web scalables, simples et indépendants des plateformes. Les API REST sont largement utilisées pour connecter des systèmes, des applications mobiles, et des services cloud.

---

## Concepts clés

### Principes fondamentaux de REST

1. **Stateless** : Chaque requête HTTP contient toutes les informations nécessaires pour être traitée. Le serveur ne conserve pas d'état entre les requêtes.
2. **Uniformité** : Les API REST utilisent des conventions standardisées (ex. verbes HTTP, codes de statut).
3. **Cacheabilité** : Les réponses peuvent être mises en cache pour améliorer les performances.
4. **Couplage faible** : Les clients et serveurs sont indépendants, ce qui facilite la scalabilité et la maintenance.

### Enjeux pour les développeurs

1. **Conception** : Créer des endpoints clairs et cohérents pour simplifier l'utilisation de l'API.
2. **Performance** : Optimiser les réponses pour réduire la latence et la consommation de bande passante.
3. **Sécurité** : Protéger les données avec des mécanismes comme HTTPS, OAuth2, et JWT.
4. **Documentation** : Fournir une documentation complète pour faciliter l'intégration des clients.

### Convention de nommage des ressources

Dans les API REST, les ressources sont généralement nommées au pluriel pour refléter leur nature collective. Par exemple :

- `/users` : Endpoint pour gérer les utilisateurs.
- `/products` : Endpoint pour gérer les produits.
- `/orders` : Endpoint pour gérer les commandes.

Cela permet de maintenir une cohérence dans la conception des endpoints et de clarifier leur objectif. Les actions spécifiques sur une ressource individuelle sont ensuite définies par l'ID ou un identifiant unique :

- `GET /users` : Récupère tous les utilisateurs.
- `GET /users/1` : Récupère l'utilisateur avec l'ID 1.
- `POST /users` : Crée un nouvel utilisateur.
- `PUT /users/1` : Met à jour l'utilisateur avec l'ID 1.
- `DELETE /users/1` : Supprime l'utilisateur avec l'ID 1.

---

## Commandes essentielles

### Requêtes HTTP courantes

```bash
curl -X GET http://example.com/api/users          # Récupère une ressource
curl -X POST -d '{"name":"Alice"}' http://example.com/api/users # Crée une ressource
curl -X PUT -d '{"name":"Alice Updated"}' http://example.com/api/users/1 # Met à jour une ressource
curl -X DELETE http://example.com/api/users/1       # Supprime une ressource
```

### En-têtes HTTP

```bash
curl -H "Authorization: Bearer <token>" http://example.com/api/resource # Ajoute un en-tête d'autorisation
curl -H "Content-Type: application/json" -X POST -d '{"key":"value"}' http://example.com/api/resource # Spécifie le type de contenu
```

### Codes de statut HTTP

- `200 OK` : Requête réussie.
- `201 Created` : Ressource créée avec succès.
- `400 Bad Request` : Requête invalide.
- `401 Unauthorized` : Authentification requise.
- `403 Forbidden` : Accès refusé.
- `404 Not Found` : Ressource introuvable.
- `500 Internal Server Error` : Erreur côté serveur.

---

## Exemples pratiques

### Exemple de requête GET

```bash
curl -X GET http://example.com/api/users
```

### Exemple de requête POST

```bash
curl -X POST -H "Content-Type: application/json" -d '{"name":"Alice","email":"alice@example.com"}' http://example.com/api/users
```

### Exemple de requête PUT

```bash
curl -X PUT -H "Content-Type: application/json" -d '{"name":"Alice Updated"}' http://example.com/api/users/1
```

### Exemple de requête DELETE

```bash
curl -X DELETE http://example.com/api/users/1
```

### Pagination des résultats

```bash
curl -X GET "http://example.com/api/users?page=2&limit=10"
```

### Filtrage des données

```bash
curl -X GET "http://example.com/api/users?role=admin"
```

---

## Bonnes pratiques

1. **Respecter les verbes HTTP** : Utilisez les verbes HTTP (`GET`, `POST`, `PUT`, `DELETE`) de manière appropriée pour refléter les actions.
2. **Utiliser des codes de statut HTTP** : Retournez des codes de statut HTTP (`200 OK`, `201 Created`, `404 Not Found`, `500 Internal Server Error`) pour indiquer le résultat des requêtes.
3. **Documenter l'API** : Utilisez des outils comme Swagger ou Postman pour documenter et tester votre API.
4. **Sécuriser l'API** : Implémentez des mécanismes d'authentification et d'autorisation (ex. OAuth2, JWT).
5. **Pagination et filtrage** : Fournissez des mécanismes pour limiter les résultats et filtrer les données.
6. **Versionner l'API** : Incluez une version dans l'URL (ex. `/v1/resource`) pour gérer les évolutions de l'API.

---

## Outils utiles

1. **Test des API REST** :
   - **Postman** : Interface graphique pour tester les requêtes HTTP.
   - **cURL** : Outil en ligne de commande pour tester les requêtes HTTP.
   - **Insomnia** : Alternative à Postman pour tester les API.

2. **Documentation des API** :
   - **Swagger/OpenAPI** : Génération automatique de documentation interactive.
   - **Redoc** : Générateur de documentation basé sur OpenAPI.

3. **Sécurité des API** :
   - **OAuth2** : Protocole d'autorisation pour sécuriser les accès.
   - **JWT** : Jetons pour authentifier les utilisateurs.

---

## Liens utiles

- [Documentation REST](https://restfulapi.net/)
- [Tutoriels REST](https://www.tutorialspoint.com/restful/index.htm)
- [Outils pour tester les API REST](https://www.postman.com/)
- [Swagger/OpenAPI](https://swagger.io/)
