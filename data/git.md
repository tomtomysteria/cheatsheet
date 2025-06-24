# 📦 Git

## Introduction

Git est un système de contrôle de version distribué qui permet de suivre les modifications apportées au code source, de collaborer efficacement et de gérer les versions des projets.

---

## Commandes essentielles

### Initialisation et configuration

```bash
git init                     # Initialise un dépôt Git
git config --global user.name "Votre Nom"  # Configure le nom d'utilisateur
git config --global user.email "votre.email@example.com"  # Configure l'email
```

### Gestion des fichiers

```bash
git add <file>               # Ajoute un fichier au suivi
git add .                    # Ajoute tous les fichiers modifiés
git commit -m "Message"      # Enregistre les modifications avec un message
git status                   # Affiche l'état du dépôt
git log                      # Affiche l'historique des commits
```

### Branches

```bash
git branch                   # Liste les branches
git branch <branch-name>     # Crée une nouvelle branche
git checkout <branch-name>   # Change de branche
git merge <branch-name>      # Fusionne une branche dans la branche actuelle
```

### Collaboration

```bash
git remote add origin <url>  # Ajoute un dépôt distant
git push origin <branch-name> # Pousse les modifications vers le dépôt distant
git pull origin <branch-name> # Récupère les modifications du dépôt distant
```

---

## Commandes avancées

### Réinitialisation et restauration

```bash
git reset --hard <commit-id> # Réinitialise le dépôt à un commit spécifique
git restore <file>           # Restaure un fichier modifié
```

### Gestion des tags

```bash
git tag <tag-name>           # Crée un tag
git push origin <tag-name>   # Pousse un tag vers le dépôt distant
```

### Recherche et comparaison

```bash
git diff                     # Compare les modifications non validées
git blame <file>             # Affiche l'historique des modifications ligne par ligne
```

---

## Exemples pratiques

### Workflow Git classique

1. **Initialisation** :

   ```bash
   git init
   ```

2. **Ajout de fichiers** :

   ```bash
   git add .
   git commit -m "Initial commit"
   ```

3. **Création d'une branche** :

   ```bash
   git branch feature-branch
   git checkout feature-branch
   ```

4. **Fusion de la branche** :

   ```bash
   git checkout main
   git merge feature-branch
   ```

### Résolution de conflits

Lorsqu'un conflit survient, Git marque les zones conflictuelles dans les fichiers. Résolvez les conflits, puis :

```bash
git add <file>
git commit -m "Résolution des conflits"
```

---

## Bonnes pratiques

1. **Utiliser des messages de commit clairs** : Décrivez brièvement les modifications apportées.
2. **Travailler avec des branches** : Utilisez des branches pour isoler les fonctionnalités ou les corrections.
3. **Vérifier avant de pousser** : Utilisez `git status` et `git diff` pour vérifier les modifications avant de les pousser.

---

## Liens utiles

- [Documentation officielle Git](https://git-scm.com/doc)
- [Guide GitHub](https://guides.github.com/introduction/git-handbook/)
- [Tutoriels Git](https://www.atlassian.com/git/tutorials)
