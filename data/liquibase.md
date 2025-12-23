# 📦 Liquibase

## Introduction

Liquibase est un outil de **gestion de migrations de base de données** (schema versioning). Il applique des **changesets** versionnés pour faire évoluer le schéma de manière contrôlée.

Cas d’usage :

- migrations reproductibles (dev → prod)
- historisation des changements
- rollback (selon stratégie)

---

## Concepts clés

### Changelog / changeset

- **changelog** : fichier racine (XML/YAML/JSON/SQL formaté) qui liste les changesets.
- **changeset** : unité de changement (id + author) appliquée une seule fois.

### Format SQL “Liquibase formatted SQL”

Exemple :

```sql
--liquibase formatted sql

--changeset alice:001
CREATE TABLE users (
  id BIGSERIAL PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL
);

--changeset alice:002
ALTER TABLE users ADD COLUMN created_at TIMESTAMP NOT NULL DEFAULT NOW();
```

### Table de suivi

Liquibase stocke l’historique dans `DATABASECHANGELOG` (et lock dans `DATABASECHANGELOGLOCK`).

---

## Intégration Spring Boot

Souvent via la dépendance :

- `org.liquibase:liquibase-core`

Propriétés (exemple) :

```properties
spring.liquibase.change-log=classpath:/db/changelog/db.changelog-master.yaml
spring.liquibase.enabled=true
```

### Structure de dossiers (courante)

```text
src/main/resources/
  db/
    changelog/
      db.changelog-master.yaml
      changes/
        001-init.yaml
        002-add-created-at.yaml
```

### Exemple minimal de `db.changelog-master.yaml`

```yaml
databaseChangeLog:
  - include:
      file: db/changelog/changes/001-init.yaml
  - include:
      file: db/changelog/changes/002-add-created-at.yaml
```

Astuce : en Spring Boot, le chemin est souvent relatif au classpath (`classpath:/...`).

### Exemple de changeset YAML (simple)

```yaml
databaseChangeLog:
  - changeSet:
      id: 001
      author: alice
      changes:
        - createTable:
            tableName: users
            columns:
              - column:
                  name: id
                  type: BIGINT
                  constraints:
                    primaryKey: true
                    nullable: false
              - column:
                  name: email
                  type: VARCHAR(255)
                  constraints:
                    nullable: false
                    unique: true
```

---

## Commandes essentielles (CLI)

> Selon l’installation, la CLI peut être `liquibase`.

```bash
liquibase --version

liquibase \
  --url="jdbc:postgresql://localhost:5432/mydb" \
  --username="user" \
  --password="pass" \
  --changeLogFile="db/changelog/db.changelog-master.yaml" \
  update
```

Rollback (si défini) :

```bash
liquibase rollbackCount 1
```

---

## Bonnes pratiques

1. **Un changeset = une intention** (petit, lisible).
2. **Ne jamais modifier un changeset appliqué** (sinon checksum mismatch) : créer un nouveau changeset.
3. **Préférer des migrations compatibles** (expand/contract) pour limiter les downtime.
4. **Context/labels** pour activer certains changesets selon l’environnement.
5. **Index et contraintes** : penser perf et intégrité.

6. **Zéro-downtime (expand/contract)** : ajouter colonne nullable → backfill → rendre NOT NULL → supprimer l’ancien champ plus tard.

---

## Liens utiles

- [Liquibase](https://docs.liquibase.com/)
- [Spring Boot + Liquibase](https://docs.spring.io/spring-boot/docs/current/reference/html/howto.html#howto.data-initialization)
