# 📦 Composer

## Introduction

Composer est un gestionnaire de dépendances pour PHP. Il permet de gérer les bibliothèques et les packages nécessaires à un projet, simplifiant ainsi le développement et la maintenance des applications PHP.

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

---

## Bonnes pratiques

1. **Versionner composer.json** : Ajoutez `composer.json` et `composer.lock` à votre contrôle de version pour garantir la cohérence des dépendances.
2. **Utiliser des versions spécifiques** : Spécifiez les versions des packages pour éviter les incompatibilités.
3. **Nettoyer les dépendances** : Supprimez les dépendances inutilisées pour réduire la taille du projet.

---

## Liens utiles

- [Documentation officielle Composer](https://getcomposer.org/doc/)
- [Packagist - Répertoire des packages](https://packagist.org/)
