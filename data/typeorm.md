# 📦 TypeORM

## Introduction

TypeORM est un ORM (Object-Relational Mapping) pour Node.js et TypeScript. Il permet de gérer les bases de données relationnelles de manière intuitive en utilisant des entités et des migrations.

---

## Commandes essentielles

### Installation et configuration

```bash
npm install typeorm reflect-metadata  # Installe TypeORM et ses dépendances
npm install mysql                     # Installe le driver MySQL (ou un autre driver comme `pg` pour PostgreSQL)
typeorm init --name my-project --database mysql  # Initialise un projet TypeORM
```

### Gestion des migrations

```bash
typeorm migration:create -n CreateUsersTable  # Crée une nouvelle migration
typeorm migration:run                        # Exécute les migrations
typeorm migration:revert                     # Annule la dernière migration
```

---

## Exemples pratiques

### Exemple d'entité

```typescript
import { Entity, PrimaryGeneratedColumn, Column } from 'typeorm';

@Entity()
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  name: string;

  @Column({ unique: true })
  email: string;

  @Column({ default: true })
  isActive: boolean;
}
```

### Exemple de migration

```typescript
import { MigrationInterface, QueryRunner } from 'typeorm';

export class CreateUsersTable1651234567890 implements MigrationInterface {
  public async up(queryRunner: QueryRunner): Promise<void> {
    await queryRunner.query(`
      CREATE TABLE users (
        id INT AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(100) NOT NULL,
        email VARCHAR(100) UNIQUE NOT NULL,
        isActive BOOLEAN DEFAULT TRUE
      )
    `);
  }

  public async down(queryRunner: QueryRunner): Promise<void> {
    await queryRunner.query(`DROP TABLE users`);
  }
}
```

### Utilisation du Repository

```typescript
import { getRepository } from 'typeorm';
import { User } from './entity/User';

async function getUsers() {
  const userRepository = getRepository(User);
  const users = await userRepository.find();
  console.log(users);
}

async function createUser() {
  const userRepository = getRepository(User);
  const user = userRepository.create({ name: 'Alice', email: 'alice@example.com' });
  await userRepository.save(user);
}
```

---

## Bonnes pratiques

1. **Utiliser les migrations** : Gérez les modifications de schéma avec des migrations pour garantir la cohérence des bases de données.
2. **Activer les logs** : Configurez TypeORM pour afficher les requêtes SQL exécutées.

   ```typescript
   const connection = await createConnection({
     logging: true,
   });
   ```

3. **Utiliser les relations** : Implémentez des relations entre les entités pour simplifier les requêtes complexes.

---

## Liens utiles

- [Documentation officielle TypeORM](https://typeorm.io/)
- [Tutoriels TypeORM](https://typeorm.io/#/tutorials)
- [Exemples de projets TypeORM](https://github.com/typeorm/typeorm/tree/master/sample)
