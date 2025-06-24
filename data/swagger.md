# 📦 Swagger

## Introduction

Swagger est un outil open-source pour documenter, concevoir, et tester les API REST. Il simplifie la collaboration entre les développeurs et les équipes en fournissant une interface interactive pour explorer les endpoints.

---

## Commandes essentielles

### Installation

```bash
npm install swagger-ui-express       # Installe Swagger pour Express.js
npm install @nestjs/swagger          # Installe Swagger pour Nest.js
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
            "description": "Liste des utilisateurs"
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
import { ApiTags, ApiOperation, ApiResponse } from '@nestjs/swagger';

@ApiTags('users')
@Controller('users')
export class UsersController {
  @ApiOperation({ summary: 'Récupère la liste des utilisateurs' })
  @ApiResponse({ status: 200, description: 'Liste des utilisateurs.' })
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

---

## Liens utiles

- [Documentation officielle Swagger](https://swagger.io/docs/)
- [Tutoriels Swagger](https://swagger.io/tools/swaggerhub/)
- [Exemples de projets Swagger](https://github.com/swagger-api/swagger-samples)
