# 🔐 Authentification et Autorisation

## Introduction

L'authentification et l'autorisation sont des concepts fondamentaux pour sécuriser les applications et contrôler l'accès aux ressources. Bien qu'ils soient souvent utilisés ensemble, ils remplissent des rôles distincts.

---

## Authentification

L'authentification est le processus de vérification de l'identité d'un utilisateur ou d'un système. Elle permet de s'assurer que l'utilisateur est bien celui qu'il prétend être.

### Types d'authentification

1. **Mot de passe** :
   - L'utilisateur fournit un identifiant et un mot de passe.
   - Exemple : Connexion à un site web.

2. **Multi-facteurs (MFA)** :
   - Combine plusieurs facteurs comme un mot de passe et un code envoyé par SMS.
   - Exemple : Connexion sécurisée aux services bancaires.

3. **Tokens (JWT)** :
   - Utilise des tokens pour une authentification stateless.
   - Exemple : API REST.

4. **Biométrie** :
   - Utilise des caractéristiques physiques comme les empreintes digitales.
   - Exemple : Déverrouillage d'un smartphone.

---

## Autorisation

L'autorisation est le processus de contrôle des accès. Elle détermine les actions qu'un utilisateur ou un système est autorisé à effectuer après avoir été authentifié.

### Types d'autorisation

1. **Basée sur les rôles (RBAC)** :
   - Les permissions sont attribuées en fonction des rôles.
   - Exemple : Un administrateur peut gérer les utilisateurs, mais un utilisateur standard ne peut pas.

2. **Basée sur les attributs (ABAC)** :
   - Les permissions sont attribuées en fonction des attributs comme l'âge ou la localisation.
   - Exemple : Accès à des ressources spécifiques selon la localisation géographique.

3. **Listes de contrôle d'accès (ACL)** :
   - Les permissions sont définies pour chaque utilisateur ou groupe.
   - Exemple : Accès à des fichiers spécifiques sur un serveur.

---

## Différence entre Authentification et Autorisation

| **Authentification** | **Autorisation** |
|-----------------------|-------------------|
| Vérifie l'identité. | Contrôle les actions. |
| "Qui êtes-vous ?" | "Que pouvez-vous faire ?" |
| Exemple : Connexion. | Exemple : Accès à une ressource. |

---

## OIDC et OAuth

### Qu'est-ce que OAuth ?

OAuth (Open Authorization) est un protocole standard qui permet à une application d'accéder aux ressources d'un utilisateur sur un autre service, sans avoir à partager ses identifiants.

#### Fonctionnement de OAuth

1. **Autorisation** : L'utilisateur autorise l'application à accéder à ses données.
2. **Token d'accès** : L'application reçoit un token d'accès pour interagir avec l'API du service.
3. **Scopes** : Définissent les permissions accordées (exemple : lecture des emails).

#### Exemple de OAuth

- Une application tierce accède à votre compte Google pour récupérer vos contacts.

### Qu'est-ce que OIDC ?

OIDC (OpenID Connect) est une couche d'identité construite sur OAuth 2.0. Elle permet l'authentification des utilisateurs et fournit des informations sur leur identité.

#### Fonctionnement de OIDC

1. **Authentification** : L'utilisateur s'authentifie auprès du fournisseur d'identité.
2. **Token ID** : Un token ID est généré, contenant des informations sur l'utilisateur (nom, email, etc.).
3. **Interopérabilité** : Permet aux applications de vérifier l'identité de l'utilisateur.

#### Exemple de OIDC

- Connexion à une application via "Se connecter avec Google".

### Différence entre OAuth et OIDC

| **OAuth** | **OIDC** |
|-----------|----------|
| Fournit un accès aux ressources. | Fournit une authentification et des informations sur l'identité. |
| Utilisé pour l'autorisation. | Utilisé pour l'authentification. |
| Exemple : Accès aux fichiers Google Drive. | Exemple : Connexion via Google. |

---

## Bearer Tokens

Les Bearer Tokens sont des jetons d'accès utilisés pour authentifier et autoriser les requêtes dans les systèmes sécurisés. Ils sont souvent utilisés dans les API REST et les systèmes basés sur OAuth.

### Fonctionnement

1. **Obtention du token** :
   - L'utilisateur ou l'application obtient un Bearer Token après une authentification réussie.
   - Ce token est généralement délivré par un serveur d'autorisation.

2. **Utilisation du token** :
   - Le token est inclus dans l'en-tête HTTP `Authorization` avec le préfixe `Bearer`.
   - Exemple : `Authorization: Bearer <token>`

3. **Validation du token** :
   - Le serveur valide le token pour s'assurer qu'il est authentique et non expiré.
   - Si le token est valide, l'accès est accordé.

### Avantages

- **Stateless** : Les Bearer Tokens permettent une authentification sans état, ce qui réduit la charge sur le serveur.
- **Interopérabilité** : Ils peuvent être utilisés avec différents systèmes et plateformes.
- **Sécurité** : Les tokens peuvent être signés et chiffrés pour garantir leur intégrité.

### Bonnes pratiques pour les Bearer Tokens

1. **Utiliser HTTPS** :
   - Toujours transmettre les tokens via des connexions sécurisées.

2. **Configurer une expiration** :
   - Définir une durée de vie appropriée pour les tokens afin de limiter les risques en cas de compromission.

3. **Révoquer les tokens compromis** :
   - Mettre en place un mécanisme pour invalider les tokens en cas de compromission.

4. **Limiter les permissions** :
   - Appliquer le principe du moindre privilège en définissant des scopes précis.

5. **Stocker les tokens de manière sécurisée** :
   - Ne jamais exposer les tokens dans le code source ou les journaux.

---

## Bonnes pratiques

1. **Sécuriser les mots de passe** :
   - Utiliser des algorithmes de hachage comme bcrypt.
   - Ne jamais stocker les mots de passe en clair.

2. **Utiliser des tokens sécurisés** :
   - Signer les tokens avec une clé secrète.
   - Définir une durée d'expiration pour les tokens.

3. **Mettre en place MFA** :
   - Ajouter une couche de sécurité supplémentaire.

4. **Limiter les permissions** :
   - Appliquer le principe du moindre privilège.
   - Ne donner que les permissions nécessaires.

5. **Auditer les accès** :
   - Surveiller les actions des utilisateurs.
   - Identifier les tentatives d'accès non autorisées.

---

## Bonnes pratiques pour OAuth et OIDC

1. **Utiliser HTTPS** : Toujours sécuriser les communications.
2. **Limiter les scopes** : Ne demander que les permissions nécessaires.
3. **Configurer les expirations de tokens** : Définir une durée de vie appropriée pour les tokens.
4. **Auditer les accès** : Surveiller les tokens et les permissions accordées.

---

## SAML (Security Assertion Markup Language)

SAML est un protocole utilisé pour l'authentification et l'autorisation, souvent dans les environnements d'entreprise.

### Pertinence pour SAML

- Idéal pour les entreprises ayant besoin d'une solution d'authentification unique (SSO).
- Permet une interopérabilité entre différents systèmes.

### Recommandations pour SAML

- Utiliser SAML pour les applications nécessitant une intégration avec des fournisseurs d'identité.
- Configurer des assertions SAML signées pour garantir la sécurité.

---

## JWT (JSON Web Tokens)

Les JWT sont des tokens utilisés pour l'authentification stateless.

### Pertinence pour JWT

- Idéal pour les API REST et les systèmes distribués.
- Permet une authentification rapide et sans état.

### Recommandations pour JWT

- Utiliser des algorithmes sécurisés comme RS256.
- Configurer une expiration pour limiter les risques en cas de compromission.

---

## OAuth 1.0 vs OAuth 2.0

### Pertinence pour OAuth 1.0 vs OAuth 2.0

- OAuth 2.0 est recommandé pour la plupart des cas modernes en raison de sa simplicité et de sa flexibilité.
- OAuth 1.0 peut être utilisé dans des environnements nécessitant des signatures HMAC.

### Recommandations pour OAuth 1.0 vs OAuth 2.0

- Privilégier OAuth 2.0 pour les nouvelles implémentations.
- Utiliser PKCE avec OAuth 2.0 pour renforcer la sécurité.

---

## Authentification basée sur les certificats

### Pertinence pour l'authentification basée sur les certificats

- Idéal pour les systèmes nécessitant une sécurité élevée, comme les réseaux internes.
- Utilisé pour l'authentification des machines et des appareils.

### Recommandations pour l'authentification basée sur les certificats

- Configurer des certificats client pour les systèmes critiques.
- Utiliser des autorités de certification fiables.

---

## Authentification déléguée

### Pertinence pour l'authentification déléguée

- Utile pour les administrateurs et les systèmes nécessitant des actions au nom d'un utilisateur.
- Permet une gestion flexible des accès.

### Recommandations pour l'authentification déléguée

- Limiter l'utilisation de l'impersonation pour des raisons de sécurité.
- Auditer les actions effectuées via l'authentification déléguée.

---

## Gestion des sessions

### Pertinence pour la gestion des sessions

- Essentiel pour les applications web nécessitant une gestion des utilisateurs connectés.
- Permet de sécuriser les interactions utilisateur.

### Recommandations pour la gestion des sessions

- Utiliser des sessions basées sur les tokens pour les systèmes distribués.
- Configurer une expiration pour les sessions.

---

## Authentification Zero Trust

### Pertinence pour l'authentification Zero Trust

- Recommandé pour les environnements modernes nécessitant une sécurité renforcée.
- Idéal pour les entreprises adoptant une approche de sécurité proactive.

### Recommandations pour l'authentification Zero Trust

- Implémenter une vérification continue des utilisateurs et des appareils.
- Utiliser la micro-segmentation pour limiter les accès.

---

## OAuth Device Flow

### Pertinence pour OAuth Device Flow

- Idéal pour les appareils sans interface utilisateur, comme les téléviseurs connectés.
- Simplifie l'authentification pour les utilisateurs.

### Recommandations pour OAuth Device Flow

- Configurer des codes d'appareil sécurisés.
- Limiter les permissions accordées via le Device Flow.

---

## PKCE (Proof Key for Code Exchange)

### Pertinence pour PKCE

- Recommandé pour renforcer la sécurité des flux OAuth 2.0.
- Protège contre les attaques de type interception.

### Recommandations pour PKCE

- Toujours utiliser PKCE avec les applications publiques.
- Configurer des codes challenge et verifier robustes.

---

## Authentification sociale

### Pertinence pour l'authentification sociale

- Idéal pour simplifier l'inscription et la connexion des utilisateurs.
- Permet une intégration rapide avec des fournisseurs populaires.

### Recommandations pour l'authentification sociale

- Utiliser des fournisseurs d'identité fiables comme Google ou Facebook.
- Limiter les permissions demandées pour respecter la vie privée des utilisateurs.

---

## Interaction entre OAuth et JWT

OAuth et JWT sont souvent utilisés ensemble pour gérer l'autorisation et l'authentification dans les systèmes modernes.

### Fonctionnement de l'interaction OAuth et JWT

1. **OAuth pour l'autorisation** :
   - OAuth est utilisé pour permettre à une application d'accéder aux ressources d'un utilisateur sur un autre service.
   - Lorsqu'un utilisateur autorise une application, un token d'accès est généré.

2. **Bearer Token comme mécanisme d'accès** :
   - Le token d'accès généré par OAuth est généralement un Bearer Token.
   - Ce Bearer Token est utilisé pour authentifier les requêtes auprès du service.

3. **JWT comme format du Bearer Token** :
   - Dans de nombreux systèmes modernes, le Bearer Token est implémenté sous forme de JWT.
   - Les JWT permettent de transmettre des informations de manière sécurisée et stateless.

### Avantages de l'utilisation de JWT avec OAuth

- **Stateless** : Les JWT permettent une authentification sans état, réduisant la charge sur le serveur.
- **Interopérabilité** : Les JWT sont compatibles avec différents systèmes et plateformes.
- **Sécurité** : Les JWT peuvent être signés et chiffrés pour garantir leur intégrité.

### Bonnes pratiques pour OAuth et JWT

1. **Utiliser des algorithmes sécurisés** :
   - Signer les JWT avec des algorithmes comme RS256.

2. **Configurer une expiration** :
   - Définir une durée de vie appropriée pour les tokens afin de limiter les risques en cas de compromission.

3. **Transmettre via HTTPS** :
   - Toujours transmettre les tokens via des connexions sécurisées.

---

## Bearer Token et JWT

Un Bearer Token peut être un JWT, mais ce n'est pas toujours le cas. Voici les distinctions principales :

1. **Bearer Token** :
   - Type de jeton utilisé pour l'autorisation.
   - Transmis dans l'en-tête HTTP `Authorization` avec le préfixe `Bearer`.
   - Exemple : `Authorization: Bearer <token>`.
   - Peut être un identifiant opaque ou un JWT.

2. **JWT (JSON Web Token)** :
   - Format spécifique de jeton structuré en trois parties : Header, Payload, et Signature.
   - Contient des informations encodées (claims) comme l'identité de l'utilisateur et les permissions.
   - Souvent utilisé comme Bearer Token dans les systèmes modernes.

### Relation entre Bearer Token et JWT

- Un Bearer Token peut être un JWT, mais il peut aussi être un autre type de jeton (par exemple, un identifiant opaque généré par le serveur).
- Les JWT sont souvent utilisés comme Bearer Tokens car ils permettent une authentification stateless et contiennent des informations utiles.

### Exemple

- **Bearer Token opaque** : `Authorization: Bearer abc123xyz`
- **Bearer Token JWT** : `Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c`

---

## Liens utiles

- [Documentation OAuth](https://oauth.net/)
- [Documentation OIDC](https://openid.net/connect/)
- [Documentation JWT](https://jwt.io/)
- [Tutoriels sur l'authentification et l'autorisation](https://www.tutorialspoint.com/authentication_and_authorization/index.htm)
- [Documentation Bearer Tokens](https://oauth.net/2/bearer-tokens/)
