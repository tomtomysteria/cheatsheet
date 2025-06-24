# 📦 Symfony

## Introduction

Symfony est un framework PHP robuste et flexible pour le développement d'applications web. Il offre une architecture modulaire, des outils intégrés, et une communauté active, ce qui en fait un choix idéal pour les projets complexes.

---

## Commandes essentielles

### Installation et gestion de projet

```bash
composer create-project symfony/skeleton my-project       # Crée un nouveau projet Symfony
symfony server:start                                      # Démarre le serveur Symfony
symfony console list                                      # Liste les commandes disponibles
```

### Gestion des bundles

```bash
composer require <bundle-name>                            # Installe un bundle
composer remove <bundle-name>                             # Supprime un bundle
```

---

## Exemples pratiques

### Exemple de contrôleur

```php
namespace App\Controller;

use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Annotation\Route;

class HelloController {
    #[Route('/hello', name: 'hello')]
    public function index(): Response {
        return new Response('<h1>Hello, Symfony!</h1>');
    }
}
```

### Configuration de la base de données

Ajoutez les paramètres de connexion dans `.env` :

```env
DATABASE_URL="mysql://root:password@127.0.0.1:3306/mydb"
```

### Création d'une entité avec Doctrine

```bash
symfony console make:entity User
```

Exemple d'entité générée :

```php
namespace App\Entity;

use Doctrine\ORM\Mapping as ORM;

#[ORM\Entity]
class User {
    #[ORM\Id]
    #[ORM\GeneratedValue]
    #[ORM\Column(type: 'integer')]
    private $id;

    #[ORM\Column(type: 'string', length: 100)]
    private $name;

    #[ORM\Column(type: 'string', length: 100, unique: true)]
    private $email;

    // Getters et setters
}
```

### Migration de la base de données

```bash
symfony console make:migration
symfony console doctrine:migrations:migrate
```

---

## Bonnes pratiques

1. **Utiliser les environnements** : Configurez des environnements distincts (`dev`, `prod`, `test`) pour gérer les configurations spécifiques.
2. **Documenter les routes** : Utilisez des annotations pour rendre les routes explicites et faciles à comprendre.
3. **Optimiser les performances** : Activez le cache en production avec `symfony console cache:clear`.

---

## Liens utiles

- [Documentation officielle Symfony](https://symfony.com/doc/current/index.html)
- [Tutoriels Symfony](https://symfonycasts.com/)
- [Exemples de projets Symfony](https://github.com/symfony/demo)
