# 📦 TypeORM

## Introduction

TypeORM est un ORM (Object-Relational Mapping) pour Node.js et TypeScript. Il permet de gérer les bases de données relationnelles de manière intuitive en utilisant des entités, des relations, et des migrations. TypeORM est compatible avec plusieurs bases de données comme MySQL, PostgreSQL, SQLite, et SQL Server.

---

## Concepts clés

### Pourquoi utiliser TypeORM ?

1. **Abstraction des bases de données** : TypeORM simplifie les interactions avec les bases de données en utilisant des objets et des méthodes au lieu de requêtes SQL.
2. **Gestion des relations** : TypeORM prend en charge les relations entre les entités (ex. `OneToMany`, `ManyToOne`).
3. **Migrations** : Gérez les modifications de schéma de manière structurée et versionnée.
4. **TypeScript natif** : TypeORM est conçu pour tirer parti des fonctionnalités avancées de TypeScript.

### Enjeux pour les développeurs

1. **Performance** : Optimisez les requêtes générées par TypeORM pour éviter les problèmes de performance.
2. **Gestion des relations complexes** : Implémentez des relations entre les entités pour simplifier les requêtes complexes.
3. **Sécurité** : Protégez les données sensibles en configurant correctement les connexions et les permissions.
4. **Maintenance** : Utilisez les migrations pour garantir la cohérence des bases de données entre les environnements.

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
typeorm schema:log                           # Affiche les modifications de schéma non appliquées
```

### Gestion des connexions

```typescript
import { createConnection } from 'typeorm';

const connection = await createConnection({
  type: 'mysql',
  host: 'localhost',
  port: 3306,
  username: 'root',
  password: 'password',
  database: 'mydb',
  entities: [User],
  synchronize: true, // Synchronise automatiquement le schéma (à éviter en production)
});
```

---

## Exemples pratiques

### Exemple d'entité

```typescript
import { Entity, PrimaryGeneratedColumn, Column, OneToMany } from 'typeorm';
import { Post } from './Post';

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

  @OneToMany(() => Post, (post) => post.user)
  posts: Post[];
}
```

### Exemple de relation

```typescript
import { Entity, PrimaryGeneratedColumn, Column, ManyToOne } from 'typeorm';
import { User } from './User';

@Entity()
export class Post {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  title: string;

  @Column()
  content: string;

  @ManyToOne(() => User, (user) => user.posts)
  user: User;
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
4. **Limiter `synchronize` en production** : Utilisez `synchronize: false` en production pour éviter les modifications automatiques du schéma.
5. **Optimiser les requêtes** : Utilisez les relations et les options de requête pour réduire les appels inutiles à la base de données.

---

## Outils utiles

- **TypeORM CLI** : Outil en ligne de commande pour gérer les migrations et les connexions.
- **pgAdmin** : Interface graphique pour gérer les bases de données PostgreSQL.
- **MySQL Workbench** : Interface graphique pour gérer les bases de données MySQL.
- **Postman** : Test des endpoints API connectés à TypeORM.

---

## Commandes avancées

### Analyse des performances

```typescript
const users = await getRepository(User).find({
  relations: ['posts'], // Charge les relations pour éviter les requêtes supplémentaires
});
```

### Gestion des connexions multiples

```typescript
import { createConnections } from 'typeorm';

const connections = await createConnections([
  {
    name: 'default',
    type: 'mysql',
    host: 'localhost',
    database: 'mydb',
    entities: [User],
  },
  {
    name: 'analytics',
    type: 'postgres',
    host: 'localhost',
    database: 'analytics',
    entities: [Analytics],
  },
]);
```

---

## Liens utiles

- [Documentation officielle TypeORM](https://typeorm.io/)
- [Tutoriels TypeORM](https://typeorm.io/#/tutorials)
- [Exemples de projets TypeORM](https://github.com/typeorm/typeorm/tree/master/sample)
- [pgAdmin](https://www.pgadmin.org/)
- [MySQL Workbench](https://www.mysql.com/products/workbench/)
