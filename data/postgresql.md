# 📦 PostgreSQL

## Introduction

PostgreSQL est un système de gestion de base de données relationnelle open-source réputé pour sa robustesse, ses performances, et ses fonctionnalités avancées. Il est idéal pour les applications nécessitant une gestion complexe des données.

---

## Commandes essentielles

### Connexion et gestion de base

```bash
psql -U postgres                     # Se connecter à PostgreSQL
\l                                   # Liste les bases de données
\c <database_name>                   # Se connecter à une base de données
\dt                                  # Liste les tables de la base de données
\q                                   # Quitter psql
```

### Gestion des bases de données

```bash
CREATE DATABASE mydb;                # Créer une base de données
DROP DATABASE mydb;                  # Supprimer une base de données
```

### Gestion des utilisateurs

```bash
CREATE USER myuser WITH PASSWORD 'mypassword';  # Créer un utilisateur
GRANT ALL PRIVILEGES ON DATABASE mydb TO myuser; # Accorder des privilèges à un utilisateur
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
```

### Mise à jour et suppression

```sql
UPDATE users SET name = 'Alice Updated' WHERE id = 1;
DELETE FROM users WHERE id = 1;
```

### Utilisation des index

```sql
CREATE INDEX idx_users_email ON users(email);
```

---

## Bonnes pratiques

1. **Utiliser les transactions** : Garantissez l'intégrité des données avec `BEGIN`, `COMMIT`, et `ROLLBACK`.

   ```sql
   BEGIN;
   INSERT INTO users (name, email) VALUES ('Bob', 'bob@example.com');
   COMMIT;
   ```

2. **Optimiser les performances** : Utilisez des index pour accélérer les requêtes.
3. **Sauvegarder régulièrement** : Utilisez `pg_dump` pour sauvegarder vos bases de données.

   ```bash
   pg_dump -U postgres mydb > mydb_backup.sql
   ```

---

## Liens utiles

- [Documentation officielle PostgreSQL](https://www.postgresql.org/docs/)
- [Tutoriels PostgreSQL](https://www.postgresqltutorial.com/)
- [Exemples de requêtes SQL](https://github.com/postgres/awesome-postgres)
