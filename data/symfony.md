# 📦 Symfony

## Introduction

Symfony est un framework PHP open-source conçu pour développer des applications web robustes et scalables. Il offre une architecture modulaire, des outils puissants, et une intégration facile avec des bases de données et des services tiers. Symfony est idéal pour les projets nécessitant une structure bien définie, une maintenabilité élevée, et une extensibilité grâce à ses nombreux composants.

---

## Commandes essentielles

### Symfony CLI

```bash
symfony new my-project --webapp       # Crée un nouveau projet Symfony avec une configuration web complète
symfony serve                         # Démarre le serveur de développement
symfony console make:controller       # Génère un contrôleur
symfony console make:entity           # Génère une entité
symfony console make:migration        # Génère une migration
symfony console doctrine:migrations:migrate # Applique les migrations
symfony console make:form             # Génère un formulaire
symfony console cache:clear           # Vide le cache
symfony console debug:router          # Affiche les routes disponibles
symfony console lint:twig             # Analyse les fichiers Twig pour détecter les erreurs
symfony console debug:event-dispatcher # Liste les événements disponibles
symfony console debug:container       # Affiche les services disponibles dans le conteneur
symfony console test                  # Exécute les tests
```

---

## Concepts clés

### Exemple de contrôleur

```php
// filepath: src/Controller/HelloController.php
namespace App\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Annotation\Route;

class HelloController extends AbstractController
{
    #[Route('/hello', name: 'app_hello')]
    public function index(): Response
    {
        return $this->json(['message' => 'Hello, Symfony!']);
    }
}
```

---

## Entités et ORM avec Doctrine

### Exemple d'entité

```php
// filepath: src/Entity/User.php
namespace App\Entity;

use Doctrine\ORM\Mapping as ORM;

#[ORM\Entity]
class User
{
    #[ORM\Id]
    #[ORM\GeneratedValue]
    #[ORM\Column(type: 'integer')]
    private int $id;

    #[ORM\Column(type: 'string', length: 255)]
    private string $name;

    #[ORM\Column(type: 'string', length: 255, unique: true)]
    private string $email;

    // Getters et setters...
}
```

### Exemple de repository

```php
// filepath: src/Repository/UserRepository.php
namespace App\Repository;

use App\Entity\User;
use Doctrine\Bundle\DoctrineBundle\Repository\ServiceEntityRepository;
use Doctrine\Persistence\ManagerRegistry;

class UserRepository extends ServiceEntityRepository
{
    public function __construct(ManagerRegistry $registry)
    {
        parent::__construct($registry, User::class);
    }

    public function findByEmail(string $email): ?User
    {
        return $this->findOneBy(['email' => $email]);
    }
}
```

---

## Services

### Exemple de service

```php
// filepath: src/Service/UserService.php
namespace App\Service;

use App\Repository\UserRepository;

class UserService
{
    private UserRepository $userRepository;

    public function __construct(UserRepository $userRepository)
    {
        $this->userRepository = $userRepository;
    }

    public function getUserByEmail(string $email): ?array
    {
        $user = $this->userRepository->findByEmail($email);
        if (!$user) {
            return null;
        }

        return [
            'id' => $user->getId(),
            'name' => $user->getName(),
            'email' => $user->getEmail(),
        ];
    }
}
```

---

## Vues avec Twig

### Exemple de vue Twig

```twig
<!-- filepath: templates/hello/index.html.twig -->
<!DOCTYPE html>
<html>
<head>
    <title>Symfony</title>
</head>
<body>
    <h1>{{ message }}</h1>
</body>
</html>
```

---

## Tests avec Symfony

### Utilisation de PHPUnit

Ajoutez PHPUnit au projet :

```bash
composer require --dev symfony/test-pack
```

#### Exemple de test

```php
// filepath: tests/Service/UserServiceTest.php
namespace App\Tests\Service;

use App\Repository\UserRepository;
use App\Service\UserService;
use PHPUnit\Framework\TestCase;

class UserServiceTest extends TestCase
{
    public function testGetUserByEmail()
    {
        $userRepository = $this->createMock(UserRepository::class);
        $userRepository->method('findByEmail')->willReturn(null);

        $userService = new UserService($userRepository);
        $result = $userService->getUserByEmail('test@example.com');

        $this->assertNull($result);
    }
}
```

Exécutez les tests :

```bash
symfony console test
```

---

## Gestion des logs

### Utilisation de Monolog

Ajoutez Monolog au projet :

```bash
composer require symfony/monolog-bundle
```

#### Exemple de configuration

```yaml
# filepath: config/packages/monolog.yaml
monolog:
    handlers:
        main:
            type: stream
            path: '%kernel.logs_dir%/%kernel.environment%.log'
            level: debug
```

#### Exemple d'utilisation dans un service

```php
// filepath: src/Service/LoggingService.php
namespace App\Service;

use Psr\Log\LoggerInterface;

class LoggingService
{
    private LoggerInterface $logger;

    public function __construct(LoggerInterface $logger)
    {
        $this->logger = $logger;
    }

    public function logInfo(string $message): void
    {
        $this->logger->info($message);
    }

    public function logError(string $message): void
    {
        $this->logger->error($message);
    }
}
```

---

## Bonnes pratiques

1. **Structurer les projets** : Organisez les fichiers en dossiers (ex. `Controller`, `Entity`, `Repository`, `Service`, `Form`, `Templates`) pour améliorer la maintenabilité.
2. **Utiliser les annotations** : Simplifiez la configuration des routes et des entités avec les annotations.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
4. **Activer les logs** : Configurez Monolog pour surveiller les performances et les erreurs.
5. **Utiliser les formulaires Symfony** : Simplifiez la gestion des formulaires avec le composant Form.
6. **Configurer les environnements** : Utilisez des fichiers `.env` pour gérer les variables d'environnement.
7. **Utiliser Doctrine** : Simplifiez la gestion des bases de données avec Doctrine ORM.
8. **Optimiser les performances** : Configurez le cache et utilisez les outils de profiling pour améliorer les performances.

---

## Liens utiles

- [Documentation officielle Symfony](https://symfony.com/doc/current/index.html)
- [Tutoriels Symfony](https://symfonycasts.com/)
- [Exemples de projets Symfony](https://github.com/symfony/demo)
- [Documentation Doctrine ORM](https://www.doctrine-project.org/projects/orm.html)
