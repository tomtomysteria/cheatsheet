# 📦 Nest.js

## Introduction

Nest.js est un framework Node.js pour construire des applications backend efficaces et modulaires. Il est basé sur TypeScript et utilise une architecture inspirée d'Angular, ce qui le rend idéal pour les projets complexes.

---

## Commandes essentielles

### Installation et création de projet

```bash
npm install -g @nestjs/cli               # Installe le CLI Nest.js
nest new my-app                          # Crée un nouveau projet Nest.js
npm run start                            # Démarre l'application
npm run start:dev                        # Démarre l'application en mode développement
```

### Gestion des modules

```bash
nest generate module <module-name>       # Génère un module
nest generate controller <controller-name> # Génère un contrôleur
nest generate service <service-name>     # Génère un service
```

---

## Exemples pratiques

### Exemple de contrôleur

```typescript
import { Controller, Get } from '@nestjs/common';

@Controller('users')
export class UsersController {
  @Get()
  getUsers(): string[] {
    return ['Alice', 'Bob', 'Charlie'];
  }
}
```

### Exemple de service

```typescript
import { Injectable } from '@nestjs/common';

@Injectable()
export class UsersService {
  private users = ['Alice', 'Bob', 'Charlie'];

  getAllUsers(): string[] {
    return this.users;
  }
}
```

### Exemple de module

```typescript
import { Module } from '@nestjs/common';
import { UsersController } from './users.controller';
import { UsersService } from './users.service';

@Module({
  controllers: [UsersController],
  providers: [UsersService],
})
export class UsersModule {}
```

---

## Bonnes pratiques

1. **Utiliser les modules** : Divisez votre application en modules pour une meilleure organisation et maintenabilité.
2. **Utiliser les DTOs** : Implémentez des objets de transfert de données (DTOs) pour valider les données entrantes.
3. **Configurer les middlewares** : Ajoutez des middlewares pour gérer les requêtes globales (ex. authentification, journalisation).

---

## Liens utiles

- [Documentation officielle Nest.js](https://docs.nestjs.com)
- [Tutoriels Nest.js](https://docs.nestjs.com/recipes)
- [Exemples de projets Nest.js](https://github.com/nestjs/nest/tree/master/sample)
