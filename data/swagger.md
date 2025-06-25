# 📦 Swagger

## Introduction

Swagger est un outil open-source pour documenter, concevoir, et tester les API REST. Il simplifie la collaboration entre les développeurs et les équipes en fournissant une interface interactive pour explorer les endpoints. Swagger est basé sur le standard OpenAPI, ce qui garantit une compatibilité avec de nombreux outils et frameworks.

---

## Concepts clés

### Pourquoi utiliser Swagger ?

1. **Documentation interactive** : Swagger génère une interface utilisateur interactive pour tester les endpoints.
2. **Standardisation** : Swagger utilise le format OpenAPI, garantissant une compatibilité avec les outils modernes.
3. **Collaboration** : Facilite la communication entre les développeurs backend et frontend grâce à une documentation claire.
4. **Automatisation** : Swagger peut générer automatiquement des clients API et des serveurs basés sur la documentation.

### Enjeux pour les développeurs

1. **Clarté** : Documentez chaque endpoint avec des descriptions, des exemples, et des codes de statut HTTP.
2. **Sécurité** : Configurez Swagger pour gérer l'authentification (ex. JWT, OAuth2).
3. **Versionnement** : Gérez les versions de l'API pour éviter les conflits entre les clients et les serveurs.

---

## Commandes essentielles

### Installation

```bash
npm install swagger-ui-express       # Installe Swagger pour Express.js
npm install @nestjs/swagger          # Installe Swagger pour Nest.js
npm install swagger-jsdoc            # Génère automatiquement des fichiers Swagger à partir de commentaires JSDoc
```

### Initialisation de Swagger dans Express.js

Ajoutez Swagger à votre projet Express.js :

```javascript
const swaggerUi = require('swagger-ui-express');
const swaggerDocument = require('./swagger.json');

app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(swaggerDocument));
```

### Initialisation de Swagger dans Nest.js

Ajoutez Swagger à votre projet Nest.js :

```typescript
import { SwaggerModule, DocumentBuilder } from '@nestjs/swagger';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  const config = new DocumentBuilder()
    .setTitle('API Example')
    .setDescription('Documentation de l\'API')
    .setVersion('1.0')
    .addTag('users')
    .addBearerAuth() // Ajoute l'authentification JWT
    .build();
  const document = SwaggerModule.createDocument(app, config);
  SwaggerModule.setup('api', app, document);

  await app.listen(3000);
}
bootstrap();
```

---

## Exemples pratiques

### Exemple de fichier `swagger.json`

```json
{
  "swagger": "2.0",
  "info": {
    "title": "API Example",
    "version": "1.0.0",
    "description": "Documentation de l'API"
  },
  "paths": {
    "/users": {
      "get": {
        "summary": "Récupère la liste des utilisateurs",
        "responses": {
          "200": {
            "description": "Liste des utilisateurs",
            "schema": {
              "type": "array",
              "items": {
                "type": "string"
              }
            }
          }
        }
      }
    }
  }
}
```

### Ajout de décorateurs dans Nest.js

Utilisez les décorateurs pour enrichir la documentation :

```typescript
import { ApiTags, ApiOperation, ApiResponse, ApiBearerAuth } from '@nestjs/swagger';

@ApiTags('users')
@ApiBearerAuth()
@Controller('users')
export class UsersController {
  @ApiOperation({ summary: 'Récupère la liste des utilisateurs' })
  @ApiResponse({ status: 200, description: 'Liste des utilisateurs.' })
  @ApiResponse({ status: 401, description: 'Non autorisé.' })
  @Get()
  getUsers() {
    return ['Alice', 'Bob'];
  }
}
```

---

## Bonnes pratiques

1. **Utiliser des fichiers centralisés** : Stockez la configuration Swagger dans un fichier dédié pour simplifier la gestion.
2. **Documenter chaque endpoint** : Ajoutez des descriptions, des exemples de requêtes/réponses, et des codes de statut HTTP.
3. **Activer la sécurité** : Configurez Swagger pour gérer l'authentification (ex. JWT, OAuth2).
4. **Versionner l'API** : Incluez une version dans l'URL (ex. `/v1/resource`) pour gérer les évolutions de l'API.
5. **Automatiser la génération** : Utilisez des outils comme `swagger-jsdoc` pour générer automatiquement la documentation à partir des commentaires.

---

## Outils utiles

- **Swagger UI** : Interface utilisateur interactive pour explorer les endpoints.
- **Swagger Editor** : Éditeur en ligne pour créer et modifier des fichiers OpenAPI.
- **Swagger Codegen** : Génère automatiquement des clients API et des serveurs basés sur la documentation.
- **Postman** : Alternative pour tester les endpoints documentés.

---

## Commandes avancées

### Gestion des fichiers OpenAPI

```bash
swagger-cli validate swagger.json     # Valide un fichier OpenAPI
swagger-cli bundle swagger.json -o bundled.json # Combine plusieurs fichiers OpenAPI en un seul
```

### Automatisation avec swagger-jsdoc

Ajoutez des commentaires JSDoc pour générer automatiquement la documentation Swagger :

```javascript
/**
 * @swagger
 * /users:
 *   get:
 *     summary: Récupère la liste des utilisateurs
 *     responses:
 *       200:
 *         description: Liste des utilisateurs
 */
app.get('/users', (req, res) => {
  res.json(['Alice', 'Bob']);
});
```

---

## Liens utiles

- [Documentation officielle Swagger](https://swagger.io/docs/)
- [Tutoriels Swagger](https://swagger.io/tools/swaggerhub/)
- [Exemples de projets Swagger](https://github.com/swagger-api/swagger-samples)
- [Swagger Editor](https://editor.swagger.io/)
