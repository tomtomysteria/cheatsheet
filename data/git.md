# 📦 Git

## Introduction

Git est un système de contrôle de version distribué qui permet de suivre les modifications apportées au code source, de collaborer efficacement et de gérer les versions des projets. Il est essentiel pour les équipes de développement modernes, permettant de travailler simultanément sur différentes fonctionnalités tout en conservant un historique complet des modifications.

---

## Concepts clés

### Dépôt Git

Un dépôt Git est un espace où le code source est suivi. Il peut être local ou distant (ex. GitHub, GitLab).

### Branches

Les branches permettent de travailler sur des fonctionnalités ou corrections isolées. La branche principale est souvent appelée `main` ou `master`.

### Commit

Un commit représente un instantané des modifications apportées au code. Chaque commit est identifié par un hash unique.

### Remote

Un remote est un dépôt distant où le code est partagé. Les remotes sont utilisés pour collaborer avec d'autres développeurs.

---

## Commandes essentielles

### Initialisation et configuration

```bash
git init                     # Initialise un dépôt Git
git config --global user.name "Votre Nom"  # Configure le nom d'utilisateur
git config --global user.email "votre.email@example.com"  # Configure l'email
git config --list            # Affiche la configuration actuelle
```

### Gestion des fichiers

```bash
git add <file>               # Ajoute un fichier au suivi
git add .                    # Ajoute tous les fichiers modifiés
git commit -m "Message"      # Enregistre les modifications avec un message
git status                   # Affiche l'état du dépôt
git log                      # Affiche l'historique des commits
git diff                     # Compare les modifications non validées
```

### Branches

```bash
git branch                   # Liste les branches
git branch <branch-name>     # Crée une nouvelle branche
git checkout <branch-name>   # Change de branche
git switch <branch-name>     # Alternative moderne à `checkout`
git merge <branch-name>      # Fusionne une branche dans la branche actuelle
git branch -d <branch-name>  # Supprime une branche
```

### Collaboration

```bash
git remote add origin <url>  # Ajoute un dépôt distant
git remote -v                # Liste les remotes configurés
git push origin <branch-name> # Pousse les modifications vers le dépôt distant
git pull origin <branch-name> # Récupère les modifications du dépôt distant
git fetch origin             # Récupère les modifications sans fusionner
```

---

## Commandes avancées

### Réinitialisation et restauration

```bash
git reset --hard <commit-id> # Réinitialise le dépôt à un commit spécifique
git reset --soft <commit-id> # Réinitialise tout en conservant les modifications
git restore <file>           # Restaure un fichier modifié
git stash                    # Sauvegarde temporairement les modifications
git stash pop                # Récupère les modifications sauvegardées
```

### Gestion des tags

```bash
git tag <tag-name>           # Crée un tag
git tag -a <tag-name> -m "Message" # Crée un tag annoté
git push origin <tag-name>   # Pousse un tag vers le dépôt distant
git tag -d <tag-name>        # Supprime un tag local
git push origin :refs/tags/<tag-name> # Supprime un tag distant
```

### Recherche et comparaison

```bash
git diff                     # Compare les modifications non validées
git diff <branch-name>       # Compare avec une autre branche
git blame <file>             # Affiche l'historique des modifications ligne par ligne
git show <commit-id>         # Affiche les détails d'un commit spécifique
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
4. **Sauvegarder régulièrement** : Poussez vos modifications vers un dépôt distant pour éviter les pertes de données.
5. **Nettoyer les branches** : Supprimez les branches inutilisées pour garder le dépôt organisé.

---

## Enjeux du développement avec Git

1. **Collaboration** : Git facilite le travail en équipe grâce aux branches et remotes.
2. **Historique** : Chaque modification est enregistrée, permettant de revenir à une version précédente.
3. **Gestion des conflits** : Git aide à identifier et résoudre les conflits lors des fusions.
4. **Automatisation** : Intégrez Git dans vos pipelines CI/CD pour automatiser les tests et déploiements.

---

## Liens utiles

- [Documentation officielle Git](https://git-scm.com/doc)
- [Guide GitHub](https://guides.github.com/introduction/git-handbook/)
- [Tutoriels Git](https://www.atlassian.com/git/tutorials)
- [Cheat Sheet Git](https://education.github.com/git-cheat-sheet-education.pdf)
