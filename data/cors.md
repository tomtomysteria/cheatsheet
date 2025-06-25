# 🌐 CORS (Cross-Origin Resource Sharing)

## Introduction

CORS (Cross-Origin Resource Sharing) est un mécanisme de sécurité qui permet ou restreint les requêtes provenant d'un domaine différent de celui où l'API ou la ressource est hébergée. Il est essentiel pour les applications web modernes qui interagissent avec des API.

---

## Pourquoi CORS est-il nécessaire ?

1. **Sécurité** : Empêche les requêtes non autorisées provenant de domaines externes.
2. **Interopérabilité** : Permet aux applications front-end d'accéder à des API sur des domaines différents.
3. **Contrôle des accès** : Offre une granularité pour autoriser ou bloquer des requêtes spécifiques.

---

## Fonctionnement de CORS

### Requête simple

Les requêtes simples incluent des méthodes comme `GET` ou `POST` avec des en-têtes standards.

### Pré-requête (Preflight)

Pour les requêtes complexes (comme `PUT`, `DELETE` ou avec des en-têtes personnalisés), le navigateur envoie une pré-requête `OPTIONS` pour vérifier les permissions.

### En-têtes CORS

1. **Access-Control-Allow-Origin** :
   - Spécifie les domaines autorisés à accéder à la ressource.
   - Exemple : `Access-Control-Allow-Origin: https://example.com`

2. **Access-Control-Allow-Methods** :
   - Liste des méthodes HTTP autorisées.
   - Exemple : `Access-Control-Allow-Methods: GET, POST, PUT`

3. **Access-Control-Allow-Headers** :
   - Liste des en-têtes autorisés.
   - Exemple : `Access-Control-Allow-Headers: Content-Type, Authorization`

4. **Access-Control-Max-Age** :
   - Durée de mise en cache de la pré-requête.
   - Exemple : `Access-Control-Max-Age: 3600`

---

## Configuration de CORS

### Exemple avec Node.js (Express)

```javascript
const express = require('express');
const cors = require('cors');
const app = express();

app.use(cors({
  origin: 'https://example.com',
  methods: ['GET', 'POST'],
  allowedHeaders: ['Content-Type', 'Authorization'],
}));

app.get('/data', (req, res) => {
  res.json({ message: 'CORS activé !' });
});

app.listen(3000, () => {
  console.log('Serveur démarré sur le port 3000');
});
```

### Exemple avec Spring Boot

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.CorsRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

@Configuration
public class CorsConfig {
    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**")
                        .allowedOrigins("https://example.com")
                        .allowedMethods("GET", "POST")
                        .allowedHeaders("Content-Type", "Authorization")
                        .maxAge(3600);
            }
        };
    }
}
```

---

## Enjeux de CORS

CORS est crucial pour les applications web modernes, mais il peut également introduire des défis et des risques. Voici les principaux enjeux :

1. **Sécurité des données** :
   - Empêche les attaques de type CSRF (Cross-Site Request Forgery).
   - Protège les données sensibles contre les accès non autorisés.

2. **Performance** :
   - Les pré-requêtes peuvent introduire une latence supplémentaire.
   - Une mauvaise configuration peut ralentir les interactions entre le front-end et l'API.

3. **Interopérabilité** :
   - Permet aux applications de communiquer avec des API tierces.
   - Facilite l'intégration avec des services externes.

4. **Complexité de configuration** :
   - Une configuration incorrecte peut entraîner des erreurs difficiles à diagnostiquer.
   - Nécessite une compréhension approfondie des en-têtes HTTP et des mécanismes de sécurité.

---

## Concepts avancés

### Origines multiples

CORS peut être configuré pour autoriser plusieurs origines. Cela est utile pour les applications qui doivent interagir avec plusieurs domaines.

Exemple avec Node.js :

```javascript
app.use(cors({
  origin: ['https://example.com', 'https://anotherdomain.com'],
  methods: ['GET', 'POST'],
}));
```

### Cookies et CORS

Pour permettre l'envoi de cookies avec les requêtes CORS, il est nécessaire de configurer l'en-tête `Access-Control-Allow-Credentials`.

Exemple :

```javascript
app.use(cors({
  origin: 'https://example.com',
  credentials: true,
}));
```

### Restrictions des en-têtes

Certains en-têtes, comme `Authorization`, nécessitent une configuration explicite dans `Access-Control-Allow-Headers`.

---

## Scénarios courants

### API publique

Pour une API publique, il est possible d'autoriser toutes les origines avec `*`. Cependant, cela peut poser des risques de sécurité.

Exemple :

```javascript
app.use(cors({
  origin: '*',
}));
```

### API privée

Pour une API privée, il est recommandé de limiter les origines autorisées et d'utiliser des tokens d'authentification.

Exemple :

```javascript
app.use(cors({
  origin: 'https://example.com',
  allowedHeaders: ['Authorization'],
}));
```

---

## Débogage de CORS

### Erreurs courantes

1. **Origine non autorisée** :
   - Vérifiez que l'origine est correctement configurée dans `Access-Control-Allow-Origin`.

2. **Pré-requête bloquée** :
   - Assurez-vous que les méthodes et en-têtes nécessaires sont autorisés.

3. **Cookies non envoyés** :
   - Activez `Access-Control-Allow-Credentials` et configurez l'origine de manière stricte.

### Outils de débogage

- **DevTools du navigateur** :
  - Inspectez les requêtes réseau pour vérifier les en-têtes CORS.
- **Postman** :
  - Testez les requêtes avec différentes configurations.
- **Logs serveur** :
  - Analysez les erreurs liées aux pré-requêtes.

---

## Bonnes pratiques supplémentaires

1. **Limiter les permissions** :
   - Autorisez uniquement les méthodes et en-têtes nécessaires.

2. **Configurer les délais d'expiration** :
   - Utilisez `Access-Control-Max-Age` pour réduire les pré-requêtes.

3. **Auditer régulièrement** :
   - Vérifiez les configurations CORS pour détecter les failles potentielles.

4. **Documenter les configurations** :
   - Maintenez une documentation claire pour faciliter la maintenance.

---

## Relation entre CORS et HTTPS

CORS est étroitement lié à HTTPS, bien que ce ne soit pas une exigence stricte. Voici les points importants à comprendre :

### Pourquoi utiliser HTTPS avec CORS ?

1. **Sécurisation des données** :
   - HTTPS garantit que les données échangées entre le client et le serveur sont chiffrées.
   - CORS, lorsqu'il est utilisé avec HTTPS, protège les données contre les attaques de type interception ou écoute clandestine.

2. **Confiance des origines** :
   - Les navigateurs modernes favorisent les connexions sécurisées (HTTPS) pour les requêtes CORS.
   - Une origine sécurisée (par exemple, `https://example.com`) est souvent requise pour autoriser les requêtes CORS.

3. **Prévention des attaques** :
   - L'utilisation de CORS avec HTTPS réduit les risques d'attaques comme le MITM (Man-in-the-Middle).
   - Les en-têtes CORS, combinés à HTTPS, renforcent la sécurité des API.

### Bonnes pratiques pour CORS et HTTPS

1. **Toujours utiliser HTTPS** :
   - Configurez votre serveur pour répondre uniquement aux requêtes HTTPS.
   - Exemple : Redirigez les requêtes HTTP vers HTTPS.

2. **Configurer les en-têtes CORS** :
   - Assurez-vous que les en-têtes CORS sont correctement configurés pour les connexions sécurisées.
   - Exemple : `Access-Control-Allow-Origin: https://example.com`.

3. **Limiter les origines autorisées** :
   - Ne pas utiliser `*` dans `Access-Control-Allow-Origin` pour les connexions HTTPS.
   - Autorisez uniquement les origines de confiance.

---

## Pourquoi les données ne peuvent pas être chiffrées en HTTP ?

HTTP (HyperText Transfer Protocol) ne prend pas en charge le chiffrement des données échangées entre le client et le serveur. Voici les raisons principales :

### Absence de mécanisme de sécurité

1. **Transmission en clair** :
   - Les données envoyées via HTTP sont transmises en clair, ce qui signifie qu'elles peuvent être interceptées et lues par des attaquants.

2. **Pas de support pour TLS/SSL** :
   - HTTP ne prend pas en charge les protocoles de chiffrement comme TLS (Transport Layer Security) ou SSL (Secure Sockets Layer).

### Risques liés à HTTP

1. **Interception des données** :
   - Les informations sensibles, comme les mots de passe ou les tokens, peuvent être facilement interceptées par des attaquants.

2. **Attaques MITM (Man-in-the-Middle)** :
   - Les attaquants peuvent intercepter et modifier les données échangées entre le client et le serveur.

3. **Absence de vérification d'intégrité** :
   - HTTP ne garantit pas que les données reçues par le client ou le serveur n'ont pas été altérées.

### Comparaison avec HTTPS

HTTPS (HyperText Transfer Protocol Secure) résout ces problèmes en ajoutant une couche de sécurité via TLS/SSL. Avec HTTPS :

1. **Chiffrement des données** :
   - Les données échangées sont chiffrées, ce qui les rend illisibles pour les attaquants.

2. **Authentification du serveur** :
   - HTTPS garantit que le client communique avec le serveur légitime.

3. **Intégrité des données** :
   - HTTPS assure que les données échangées n'ont pas été modifiées.

### Recommandation

Pour garantir la sécurité des données, il est fortement recommandé de migrer vers HTTPS pour tous les environnements, y compris les environnements de test et de production.

---

## Liens utiles supplémentaires

- [Guide complet sur CORS](https://www.freecodecamp.org/news/understanding-cors/)
- [Exemples pratiques de configurations CORS](https://enable-cors.org/)
