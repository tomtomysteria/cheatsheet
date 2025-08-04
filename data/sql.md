# 📦 SQL

## Introduction

SQL (Structured Query Language) est un langage standard pour interagir avec les bases de données relationnelles. Il permet de créer, lire, mettre à jour et supprimer des données, ainsi que de gérer la structure des bases de données.

---

## Concepts clés

### Pourquoi utiliser SQL ?

1. **Standardisation** : SQL est un langage standardisé pris en charge par la plupart des systèmes de gestion de bases de données relationnelles (SGBDR).
2. **Puissance** : Il permet de manipuler et interroger des données complexes avec des commandes simples.
3. **Flexibilité** : SQL prend en charge des fonctionnalités avancées comme les jointures, les sous-requêtes et les fonctions d'agrégation.
4. **Interopérabilité** : Compatible avec de nombreux outils et langages de programmation.

### Enjeux pour les développeurs

1. **Optimisation des requêtes** : Utilisez des index et analysez les plans d'exécution pour améliorer les performances.
2. **Sécurisation des données** : Implémentez des permissions et des rôles pour protéger les données sensibles.
3. **Gestion des transactions** : Garantissez l'intégrité des données avec des transactions ACID.
4. **Portabilité** : Adaptez les requêtes pour différents SGBDR.

---

## Commandes essentielles

### Gestion des bases de données

```sql
CREATE DATABASE mydb;                -- Créer une base de données
DROP DATABASE mydb;                  -- Supprimer une base de données
USE mydb;                            -- Sélectionner une base de données
```

### Gestion des tables

```sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);                                    -- Créer une table

DROP TABLE users;                     -- Supprimer une table

ALTER TABLE users ADD COLUMN age INT; -- Ajouter une colonne
ALTER TABLE users DROP COLUMN age;    -- Supprimer une colonne
```

### Insertion et requêtes

```sql
INSERT INTO users (name, email) VALUES ('Alice', 'alice@example.com');
SELECT * FROM users;
SELECT name, email FROM users WHERE created_at > NOW() - INTERVAL 7 DAY;
```

### Mise à jour et suppression

```sql
UPDATE users SET name = 'Alice Updated' WHERE id = 1;
DELETE FROM users WHERE id = 1;
```

### Utilisation des index

```sql
CREATE INDEX idx_users_email ON users(email); -- Créer un index
DROP INDEX idx_users_email;                   -- Supprimer un index
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
3. **Sauvegarder régulièrement** : Automatisez les sauvegardes pour garantir la récupération des données.
4. **Sécuriser les données** : Configurez des rôles et des permissions pour limiter l'accès aux données sensibles.
5. **Normaliser les données** : Suivez les principes de normalisation pour éviter la redondance et améliorer la cohérence.

---

## Outils utiles

- **MySQL Workbench** : Interface graphique pour gérer MySQL.
- **pgAdmin** : Interface graphique pour PostgreSQL.
- **DBeaver** : Outil universel pour gérer plusieurs types de bases de données.
- **EXPLAIN/ANALYZE** : Analyse des plans d'exécution des requêtes pour optimiser les performances.

---

## Commandes avancées

### Analyse des performances

```sql
EXPLAIN SELECT * FROM users;         -- Analyse le plan d'exécution d'une requête
EXPLAIN ANALYZE SELECT * FROM users; -- Exécute et analyse le plan d'exécution
```

### Gestion des vues

```sql
CREATE VIEW active_users AS
SELECT * FROM users WHERE active = 1; -- Créer une vue
DROP VIEW active_users;               -- Supprimer une vue
```

### Gestion des procédures stockées

```sql
DELIMITER //
CREATE PROCEDURE GetUserByEmail(IN userEmail VARCHAR(100))
BEGIN
    SELECT * FROM users WHERE email = userEmail;
END //
DELIMITER ;

CALL GetUserByEmail('alice@example.com'); -- Appeler une procédure stockée
```

---

## Liens utiles

- [Documentation officielle SQL](https://www.w3schools.com/sql/)
- [Tutoriels SQL](https://www.sqltutorial.org/)
- [Exemples de requêtes SQL](https://github.com/learn-sql/awesome-sql)
- [DBeaver](https://dbeaver.io/)
