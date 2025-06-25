# 📦 Fixtures

## Introduction

Les fixtures sont des ensembles de données statiques utilisées pour initialiser une base de données ou simuler des scénarios de test. Elles permettent de garantir des tests reproductibles et de préparer des environnements de développement. Les fixtures sont particulièrement utiles dans les tests automatisés et les environnements de staging.

---

## Concepts clés

### Pourquoi utiliser des fixtures ?

1. **Tests reproductibles** : Les fixtures garantissent que les tests s'exécutent dans des conditions identiques, réduisant les erreurs dues à des données dynamiques.
2. **Initialisation rapide** : Elles permettent de précharger des données dans une base de données pour les tests ou le développement, accélérant les cycles de développement.
3. **Simulation de scénarios** : Les fixtures peuvent simuler des cas d'utilisation spécifiques, comme des utilisateurs avec des rôles différents ou des produits avec des états variés.
4. **Isolation des tests** : Les fixtures permettent de tester des fonctionnalités indépendamment des données réelles.

---

## Commandes utiles

### TypeORM Seeding

```bash
npm install typeorm-seeding class-validator # Installe les outils nécessaires
typeorm-seeding seed                        # Exécute les seeds pour initialiser les données
typeorm-seeding seed:run                    # Lance les seeds définis dans le projet
```

### Django Fixtures

```bash
python manage.py dumpdata <app_name> > fixtures.json # Exporte les données en fixture JSON
python manage.py loaddata fixtures.json             # Charge les données depuis une fixture JSON
```

### Rails Fixtures

```bash
rails db:fixtures:load                         # Charge les fixtures dans la base de données
rails db:fixtures:create                       # Crée des fixtures pour une table
```

---

## Exemples pratiques

### Exemple de fixture en JSON

```json
[
  {
    "id": 1,
    "name": "Alice",
    "email": "alice@example.com",
    "role": "admin"
  },
  {
    "id": 2,
    "name": "Bob",
    "email": "bob@example.com",
    "role": "user"
  }
]
```

### Exemple de fixture avec TypeScript

```typescript
import { Factory, Seeder } from 'typeorm-seeding';
import { Connection } from 'typeorm';
import { User } from '../entity/User';

export default class CreateUsers implements Seeder {
  public async run(factory: Factory, connection: Connection): Promise<void> {
    await factory(User)().createMany(10); // Crée 10 utilisateurs fictifs
  }
}
```

### Exemple de fixture avec Django

```json
[
  {
    "model": "auth.user",
    "pk": 1,
    "fields": {
      "username": "admin",
      "email": "admin@example.com",
      "is_staff": true,
      "is_superuser": true
    }
  },
  {
    "model": "auth.user",
    "pk": 2,
    "fields": {
      "username": "user",
      "email": "user@example.com",
      "is_staff": false,
      "is_superuser": false
    }
  }
]
```

---

## Bonnes pratiques

1. **Utiliser des outils dédiés** : Intégrez des bibliothèques comme `typeorm-seeding`, `factory_bot` (Ruby), ou `pytest-factoryboy` (Python) pour gérer les fixtures.
2. **Documenter les fixtures** : Expliquez leur rôle et leur structure dans les commentaires ou la documentation pour faciliter leur compréhension.
3. **Nettoyer après les tests** : Supprimez les données des fixtures après chaque test pour éviter les interférences entre les tests.
4. **Limiter la taille des fixtures** : Utilisez des ensembles de données minimaux pour éviter les tests trop longs ou complexes.
5. **Automatiser la génération** : Utilisez des outils comme `factory` pour générer des données dynamiques basées sur des modèles.

---

## Outils utiles

- **TypeORM Seeding** : Génération de données pour les tests et le développement.
- **Django Fixtures** : Gestion des données statiques pour les tests.
- **Rails Fixtures** : Initialisation rapide des données dans les projets Ruby on Rails.
- **Factory Bot** : Génération de données dynamiques pour Ruby.
- **pytest-factoryboy** : Génération de données pour les tests Python.

---

## Liens utiles

- [TypeORM Seeding](https://github.com/w3tecch/typeorm-seeding)
- [Django Fixtures](https://docs.djangoproject.com/en/4.0/ref/django-admin/#loaddata)
- [Rails Fixtures](https://guides.rubyonrails.org/active_record_migrations.html#fixtures)
- [Factory Bot](https://github.com/thoughtbot/factory_bot)
- [pytest-factoryboy](https://pytest-factoryboy.readthedocs.io/)
