# 📦 REST

## Introduction

REST (Representational State Transfer) est une architecture pour les API web qui repose sur les principes HTTP. Elle permet de créer des services web scalables, simples et indépendants des plateformes.

---

## Commandes essentielles

### Requêtes HTTP courantes

```bash
curl -X GET http://example.com/api/resource          # Récupère une ressource
curl -X POST -d '{"key":"value"}' http://example.com/api/resource # Crée une ressource
curl -X PUT -d '{"key":"new_value"}' http://example.com/api/resource # Met à jour une ressource
curl -X DELETE http://example.com/api/resource       # Supprime une ressource
```

### En-têtes HTTP

```bash
curl -H "Authorization: Bearer <token>" http://example.com/api/resource # Ajoute un en-tête d'autorisation
curl -H "Content-Type: application/json" -X POST -d '{"key":"value"}' http://example.com/api/resource # Spécifie le type de contenu
```

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

---

## Bonnes pratiques

1. **Respecter les verbes HTTP** : Utilisez les verbes HTTP (`GET`, `POST`, `PUT`, `DELETE`) de manière appropriée pour refléter les actions.
2. **Utiliser des codes de statut HTTP** : Retournez des codes de statut HTTP (`200 OK`, `201 Created`, `404 Not Found`, `500 Internal Server Error`) pour indiquer le résultat des requêtes.
3. **Documenter l'API** : Utilisez des outils comme Swagger ou Postman pour documenter et tester votre API.
4. **Sécuriser l'API** : Implémentez des mécanismes d'authentification et d'autorisation (ex. OAuth2, JWT).

---

## Liens utiles

- [Documentation REST](https://restfulapi.net/)
- [Tutoriels REST](https://www.tutorialspoint.com/restful/index.htm)
- [Outils pour tester les API REST](https://www.postman.com/)
