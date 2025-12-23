# 📦 PostgreSQL

## Introduction

PostgreSQL est un système de gestion de base de données relationnelle open-source réputé pour sa robustesse, ses performances, et ses fonctionnalités avancées. Il prend en charge des fonctionnalités comme les transactions ACID, les index avancés, les types de données personnalisés, et les extensions. PostgreSQL est idéal pour les applications nécessitant une gestion complexe des données, comme les systèmes financiers, les plateformes de commerce électronique, et les applications analytiques.

---

## Concepts clés

### Pourquoi utiliser PostgreSQL ?

1. **Robustesse** : PostgreSQL garantit l'intégrité des données grâce à ses transactions ACID.
2. **Flexibilité** : Il prend en charge des types de données avancés comme JSON, XML, et les tableaux.
3. **Extensibilité** : PostgreSQL permet d'ajouter des extensions comme PostGIS pour la gestion des données géospatiales.
4. **Performance** : Optimisez les requêtes avec des index avancés et des mécanismes de caching.

### Enjeux pour les développeurs

1. **Optimisation des performances** : Configurez les index et analysez les plans d'exécution pour améliorer les performances des requêtes.
2. **Sécurisation des données** : Implémentez des rôles, des permissions, et des mécanismes de chiffrement pour protéger les données sensibles.
3. **Sauvegarde et restauration** : Automatisez les sauvegardes pour garantir la récupération des données en cas de panne.
4. **Scalabilité** : Configurez la réplication et le partitionnement pour gérer des volumes de données croissants.

---

## Commandes essentielles

### Connexion et gestion de base

```bash
psql -U postgres                     # Se connecter à PostgreSQL
\l                                   # Liste les bases de données
\c <database_name>                   # Se connecter à une base de données
\dt                                  # Liste les tables de la base de données
\di                                  # Liste les index de la base de données
\d <table_name>                      # Affiche la structure d'une table
\q                                   # Quitter psql
```

### Gestion des bases de données

```bash
CREATE DATABASE mydb;                # Créer une base de données
DROP DATABASE mydb;                  # Supprimer une base de données
ALTER DATABASE mydb SET timezone TO 'UTC'; # Modifier les paramètres d'une base de données
```

### Gestion des utilisateurs

```bash
CREATE USER myuser WITH PASSWORD 'mypassword';  # Créer un utilisateur
ALTER USER myuser WITH SUPERUSER;              # Modifier les privilèges d'un utilisateur
GRANT ALL PRIVILEGES ON DATABASE mydb TO myuser; # Accorder des privilèges à un utilisateur
REVOKE ALL PRIVILEGES ON DATABASE mydb FROM myuser; # Révoquer les privilèges d'un utilisateur
```

### Sauvegarde et restauration

```bash
pg_dump -U postgres mydb > mydb_backup.sql      # Sauvegarder une base de données
pg_restore -U postgres -d mydb mydb_backup.sql  # Restaurer une base de données
```

---

## Exemples pratiques

### Exemple de création de table

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Insertion et requêtes

```sql
INSERT INTO users (name, email) VALUES ('Alice', 'alice@example.com');
SELECT * FROM users;
SELECT name, email FROM users WHERE created_at > NOW() - INTERVAL '7 days';
```

### Mise à jour et suppression

```sql
UPDATE users SET name = 'Alice Updated' WHERE id = 1;
DELETE FROM users WHERE id = 1;
```

### Utilisation des index

```sql
CREATE INDEX idx_users_email ON users(email);
DROP INDEX idx_users_email;
```

### Transactions

```sql
BEGIN;
INSERT INTO users (name, email) VALUES ('Bob', 'bob@example.com');
ROLLBACK; -- Annule les modifications
COMMIT;   -- Valide les modifications
```

---

## Bonnes pratiques

1. **Utiliser les transactions** : Garantissez l'intégrité des données avec `BEGIN`, `COMMIT`, et `ROLLBACK`.
2. **Optimiser les performances** : Utilisez des index pour accélérer les requêtes et analysez les plans d'exécution avec `EXPLAIN`.
3. **Sauvegarder régulièrement** : Automatisez les sauvegardes avec `pg_dump` et planifiez des restaurations pour tester leur fiabilité.
4. **Sécuriser les données** : Configurez des rôles et des permissions pour limiter l'accès aux données sensibles.
5. **Partitionner les tables** : Divisez les grandes tables en partitions pour améliorer les performances.

---

## Outils utiles

- **pgAdmin** : Interface graphique pour gérer PostgreSQL.
- **PostGIS** : Extension pour la gestion des données géospatiales.
- **pg_dump/pg_restore** : Outils en ligne de commande pour la sauvegarde et la restauration.
- **EXPLAIN/ANALYZE** : Analyse des plans d'exécution des requêtes pour optimiser les performances.

---

## Commandes avancées

### Analyse des performances

```sql
EXPLAIN SELECT * FROM users;         # Analyse le plan d'exécution d'une requête
EXPLAIN ANALYZE SELECT * FROM users; # Exécute et analyse le plan d'exécution
```

### Gestion des extensions

```sql
CREATE EXTENSION IF NOT EXISTS "uuid-ossp"; # Ajoute une extension pour générer des UUID
CREATE EXTENSION IF NOT EXISTS "pgcrypto";  # Ajoute une extension pour le chiffrement
```

### Réplication et scalabilité

```bash
pg_basebackup -U postgres -D /path/to/replica -Fp -Xs -P -R # Configure une réplication
```

---

## À connaître en production

### `VACUUM` / `ANALYZE`

- `ANALYZE` met à jour les statistiques pour l’optimiseur.
- `VACUUM` limite la croissance (MVCC) et évite certains problèmes de perf.

### Locks

Certaines migrations (DDL) peuvent bloquer : penser stratégie Liquibase “expand/contract”.

### Rôles et permissions

Créer un rôle applicatif minimal (pas superuser) + droits stricts sur schémas/tables.

## Liens utiles

- [Documentation officielle PostgreSQL](https://www.postgresql.org/docs/)
- [Tutoriels PostgreSQL](https://www.postgresqltutorial.com/)
- [Exemples de requêtes SQL](https://github.com/postgres/awesome-postgres)
- [pgAdmin](https://www.pgadmin.org/)
