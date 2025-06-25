# 📦 PHP

## Introduction

PHP est un langage de programmation côté serveur largement utilisé pour développer des applications web dynamiques. Il est facile à apprendre, flexible, et offre une intégration native avec les bases de données comme MySQL. PHP est idéal pour les projets nécessitant une gestion rapide des données et une compatibilité avec les serveurs web. Grâce à des frameworks comme Laravel et Symfony, PHP permet de structurer les projets et de simplifier le développement.

---

## Commandes essentielles

### PHP CLI

```bash
php -v                                # Affiche la version de PHP
php -S localhost:8000                # Démarre un serveur web local
php composer.phar install            # Installe les dépendances via Composer
php composer.phar update             # Met à jour les dépendances
php artisan serve                    # Démarre le serveur de développement Laravel
php artisan migrate                  # Applique les migrations Laravel
php artisan make:controller <name>   # Génère un contrôleur Laravel
php artisan make:model <name>        # Génère un modèle Laravel
php artisan make:migration <name>    # Génère une migration Laravel
php artisan make:service <name>      # Génère un service Laravel (via un package tiers)
php artisan make:factory <name>      # Génère une factory Laravel
php artisan test                     # Exécute les tests Laravel
php artisan cache:clear              # Vide le cache Laravel
php artisan route:list               # Liste les routes disponibles
```

---

## Concepts clés

### Exemple de contrôleur avec Laravel

```php
// filepath: app/Http/Controllers/HelloController.php
namespace App\Http\Controllers;

use Illuminate\Http\Request;

class HelloController extends Controller
{
    public function index()
    {
        return response()->json(['message' => 'Hello, Laravel!']);
    }
}
```

---

## Modèles et ORM avec Eloquent

### Exemple de modèle

```php
// filepath: app/Models/User.php
namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class User extends Model
{
    protected $fillable = ['name', 'email'];
}
```

### Exemple de migration

```php
// filepath: database/migrations/2023_01_01_000000_create_users_table.php
use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class CreateUsersTable extends Migration
{
    public function up()
    {
        Schema::create('users', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->string('email')->unique();
            $table->timestamps();
        });
    }

    public function down()
    {
        Schema::dropIfExists('users');
    }
}
```

---

## DTOs

### Exemple de DTO

```php
// filepath: app/DTOs/UserDTO.php
namespace App\DTOs;

class UserDTO
{
    public function __construct(
        public int $id,
        public string $name,
        public string $email
    ) {}
}
```

---

## Services

### Exemple de service

```php
// filepath: app/Services/UserService.php
namespace App\Services;

use App\Models\User;
use App\DTOs\UserDTO;

class UserService
{
    public function getUserByEmail(string $email): ?UserDTO
    {
        $user = User::where('email', $email)->first();
        if (!$user) {
            return null;
        }

        return new UserDTO($user->id, $user->name, $user->email);
    }
}
```

---

## Vues avec Blade

### Exemple de vue Blade

```blade
<!-- filepath: resources/views/hello.blade.php -->
<!DOCTYPE html>
<html>
<head>
    <title>Laravel</title>
</head>
<body>
    <h1>{{ $message }}</h1>
</body>
</html>
```

---

## Tests avec PHPUnit

### Exemple de test

Ajoutez PHPUnit au projet :

```bash
composer require --dev phpunit/phpunit
```

#### Exemple de test

```php
// filepath: tests/Unit/UserServiceTest.php
namespace Tests\Unit;

use App\Models\User;
use App\Services\UserService;
use Tests\TestCase;

class UserServiceTest extends TestCase
{
    public function testGetUserByEmail()
    {
        User::factory()->create(['email' => 'test@example.com']);

        $service = new UserService();
        $user = $service->getUserByEmail('test@example.com');

        $this->assertNotNull($user);
        $this->assertEquals('test@example.com', $user->email);
    }
}
```

Exécutez les tests :

```bash
vendor/bin/phpunit
```

---

## Gestion des logs

### Utilisation de Monolog

Ajoutez Monolog au projet :

```bash
composer require monolog/monolog
```

#### Exemple d'utilisation

```php
// filepath: app/Services/LoggingService.php
namespace App\Services;

use Monolog\Logger;
use Monolog\Handler\StreamHandler;

class LoggingService
{
    private Logger $logger;

    public function __construct()
    {
        $this->logger = new Logger('app');
        $this->logger->pushHandler(new StreamHandler(storage_path('logs/app.log'), Logger::DEBUG));
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

1. **Structurer les projets** : Organisez les fichiers en dossiers (ex. `Http`, `Models`, `Services`, `Database`, `Tests`, `DTOs`, `Views`) pour améliorer la maintenabilité.
2. **Utiliser Eloquent ORM** : Simplifiez la gestion des bases de données avec Eloquent.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
4. **Activer les logs** : Configurez Monolog pour surveiller les performances et les erreurs.
5. **Utiliser les migrations** : Gérez les modifications de schéma de base de données avec les migrations.
6. **Configurer les environnements** : Utilisez des fichiers `.env` pour gérer les variables d'environnement.
7. **Optimiser les performances** : Configurez le cache et utilisez les outils de profiling pour améliorer les performances.
8. **Utiliser des DTOs** : Simplifiez le transfert de données entre les couches de l'application.

---

## Liens utiles

- [Documentation officielle PHP](https://www.php.net/docs.php)
- [Documentation Laravel](https://laravel.com/docs)
- [Tutoriels PHP](https://www.w3schools.com/php/)
- [Exemples de projets Laravel](https://github.com/laravel/laravel)
- [Documentation PHPUnit](https://phpunit.de/documentation.html)
