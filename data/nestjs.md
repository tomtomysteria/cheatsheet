# 📦 NestJS

## Introduction

NestJS est un framework Node.js basé sur TypeScript qui facilite la création d'applications backend modulaires et scalables. Il est conçu pour être extensible et utilise des concepts comme les modules, les contrôleurs, les services, les DTOs, et les entités pour structurer les applications. NestJS est idéal pour développer des API REST, des microservices, et des applications complexes.

---

## Commandes essentielles

### CLI NestJS

```bash
npm install -g @nestjs/cli                  # Installe la CLI NestJS
nest new my-app                             # Crée un nouveau projet NestJS
nest generate module <module-name>          # Génère un module
nest generate controller <controller-name>  # Génère un contrôleur
nest generate service <service-name>        # Génère un service
nest generate class <class-name> --type dto # Génère un DTO
nest generate class <class-name> --type entity # Génère une entité
nest build                                  # Compile le projet
npm run start                               # Démarre l'application
npm run start:dev                           # Démarre l'application en mode développement
npm run test                                # Exécute les tests
npm run lint                                # Analyse le code pour détecter les erreurs
```

---

## Concepts clés

### Exemple de module

```typescript
import { Module } from '@nestjs/common';
import { HelloController } from './hello.controller';
import { HelloService } from './hello.service';

@Module({
  controllers: [HelloController],
  providers: [HelloService],
})
export class HelloModule {}
```

### Exemple de contrôleur

```typescript
import { Controller, Get } from '@nestjs/common';
import { HelloService } from './hello.service';

@Controller('hello')
export class HelloController {
  constructor(private readonly helloService: HelloService) {}

  @Get()
  getHello(): string {
    return this.helloService.getHello();
  }
}
```

### Exemple de service

```typescript
import { Injectable } from '@nestjs/common';

@Injectable()
export class HelloService {
  getHello(): string {
    return 'Hello, NestJS!';
  }
}
```

---

## Modèles, DTOs et entités

### Exemple de modèle (DTO)

```typescript
export class CreateUserDto {
  readonly name: string;
  readonly email: string;
}
```

### Exemple d'entité avec TypeORM

```typescript
import { Entity, PrimaryGeneratedColumn, Column } from 'typeorm';

@Entity()
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  name: string;

  @Column()
  email: string;
}
```

### Exemple de repository avec TypeORM

```typescript
import { Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { User } from './user.entity';

@Injectable()
export class UserRepository {
  constructor(
    @InjectRepository(User)
    private readonly userRepository: Repository<User>,
  ) {}

  async findAll(): Promise<User[]> {
    return this.userRepository.find();
  }
}
```

---

## Gestion des erreurs

### Exemple de gestion des erreurs avec `HttpException`

```typescript
import { Controller, Get, HttpException, HttpStatus } from '@nestjs/common';

@Controller('error')
export class ErrorController {
  @Get()
  throwError(): void {
    throw new HttpException('Une erreur est survenue', HttpStatus.BAD_REQUEST);
  }
}
```

---

## Tests avec NestJS

### Utilisation de Jest

NestJS intègre Jest pour les tests unitaires.

Exemple de test de service :

```typescript
import { Test, TestingModule } from '@nestjs/testing';
import { HelloService } from './hello.service';

describe('HelloService', () => {
  let service: HelloService;

  beforeEach(async () => {
    const module: TestingModule = await Test.createTestingModule({
      providers: [HelloService],
    }).compile();

    service = module.get<HelloService>(HelloService);
  });

  it('devrait retourner "Hello, NestJS!"', () => {
    expect(service.getHello()).toBe('Hello, NestJS!');
  });
});
```

---

## Gestion des logs

### Utilisation de `Logger`

NestJS fournit une classe `Logger` pour gérer les logs.

```typescript
import { Injectable, Logger } from '@nestjs/common';

@Injectable()
export class LoggingService {
  private readonly logger = new Logger(LoggingService.name);

  logMessage(message: string): void {
    this.logger.log(`Message reçu : ${message}`);
  }

  logError(error: string): void {
    this.logger.error(`Erreur : ${error}`);
  }
}
```

---

## Bonnes pratiques

1. **Structurer les projets** : Organisez les projets en modules pour améliorer la maintenabilité.
2. **Utiliser les DTOs** : Validez et transférez les données avec des objets dédiés.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
4. **Activer les logs** : Configurez des logs pour surveiller les performances et les erreurs.
5. **Sécuriser les endpoints** : Utilisez des guards et des interceptors pour protéger les endpoints sensibles.
6. **Utiliser les pipes** : Implémentez des pipes pour valider et transformer les données.
7. **Utiliser TypeORM** : Simplifiez la gestion des bases de données avec TypeORM.
8. **Configurer les environnements** : Utilisez des fichiers `.env` pour gérer les configurations.

---

## Liens utiles

- [Documentation officielle NestJS](https://docs.nestjs.com/)
- [Tutoriels NestJS](https://docs.nestjs.com/first-steps)
- [Exemples de projets NestJS](https://github.com/nestjs/nest/tree/master/sample)
- [Documentation TypeScript](https://www.typescriptlang.org/docs/)
- [Documentation TypeORM](https://typeorm.io/)
