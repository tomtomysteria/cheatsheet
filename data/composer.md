# 📦 Composer

## Introduction

Composer est un gestionnaire de dépendances pour PHP. Il permet de gérer les bibliothèques et les packages nécessaires à un projet, simplifiant ainsi le développement et la maintenance des applications PHP. Il est également utilisé pour créer des projets basés sur des frameworks comme Symfony ou Laravel.

---

## Commandes essentielles

### Installation

```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

### Commandes courantes

```bash
composer install          # Installe les dépendances définies dans composer.json
composer update           # Met à jour les dépendances
composer require <package> # Ajoute un package au projet
composer remove <package> # Supprime un package du projet
composer dump-autoload    # Regénère les fichiers d'autoload
composer validate         # Valide le fichier composer.json
composer show             # Affiche les informations sur les packages installés
composer outdated         # Liste les dépendances obsolètes
```

---

## Scripts personnalisés

Composer permet de définir des scripts pour automatiser des tâches courantes.

### Exemple de script dans composer.json

```json
{
  "scripts": {
    "start": "php -S localhost:8000 -t public",
    "test": "phpunit"
  }
}
```

Exécution des scripts :

```bash
composer run-script start           # Exécute le script "start"
composer run-script test            # Exécute le script "test"
```

---

## Exemples pratiques

### Créer un projet Symfony avec Composer

```bash
composer create-project symfony/skeleton my-project
```

### Ajouter une bibliothèque

```bash
composer require monolog/monolog
```

### Supprimer une bibliothèque

```bash
composer remove monolog/monolog
```

### Exemple de fichier composer.json

```json
{
  "name": "my-project",
  "description": "Un projet PHP avec Composer",
  "require": {
    "monolog/monolog": "^2.0"
  },
  "autoload": {
    "psr-4": {
      "App\\": "src/"
    }
  },
  "scripts": {
    "start": "php -S localhost:8000 -t public",
    "test": "phpunit"
  }
}
```

### Utilisation d'une bibliothèque installée

```php
<?php
require 'vendor/autoload.php';

use Monolog\Logger;
use Monolog\Handler\StreamHandler;

$log = new Logger('name');
$log->pushHandler(new StreamHandler('app.log', Logger::WARNING));

$log->warning('Ceci est un message de warning');
?>
```

---

## Bonnes pratiques

1. **Versionner composer.json et composer.lock** : Ajoutez ces fichiers au contrôle de version pour garantir la cohérence des dépendances.
2. **Utiliser des versions spécifiques** : Spécifiez les versions des packages pour éviter les incompatibilités.
3. **Nettoyer les dépendances** : Supprimez les dépendances inutilisées pour réduire la taille du projet.
4. **Valider composer.json** : Utilisez `composer validate` pour détecter les erreurs dans le fichier de configuration.
5. **Utiliser l'autoload PSR-4** : Organisez le code en suivant les standards PSR pour simplifier l'autoloading.

---

## Liens utiles

- [Documentation officielle Composer](https://getcomposer.org/doc/)
- [Packagist - Répertoire des packages](https://packagist.org/)
- [Tutoriels Composer](https://www.tutorialspoint.com/composer/index.htm)
