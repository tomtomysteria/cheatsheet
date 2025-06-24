# 📦 Mutagen

## Introduction

Mutagen est un outil de synchronisation de fichiers conçu pour les environnements de développement. Il permet de synchroniser des fichiers entre des machines locales et distantes de manière rapide et fiable, même dans des environnements à latence élevée.

---

## Commandes essentielles

### Gestion des sessions de synchronisation

```bash
mutagen sync create /local/path remote:/path   # Crée une session de synchronisation
mutagen sync list                              # Liste les sessions actives
mutagen sync pause <session-id>                # Met en pause une session
mutagen sync resume <session-id>               # Reprend une session en pause
mutagen sync terminate <session-id>            # Supprime une session
```

### Gestion des configurations

```bash
mutagen project start                          # Démarre un projet Mutagen
mutagen project stop                           # Arrête un projet Mutagen
mutagen project list                           # Liste les projets actifs
```

---

## Exemples pratiques

### Exemple de synchronisation simple

Synchronisez un répertoire local avec un répertoire distant :

```bash
mutagen sync create /local/path user@remote:/remote/path
```

### Exemple de configuration avancée

Créez un fichier de configuration pour une synchronisation personnalisée :

```yaml
sync:
  defaults:
    mode: two-way-resolved
    ignore:
      paths:
        - ".git"
        - "node_modules"
  sessions:
    my-session:
      alpha: /local/path
      beta: user@remote:/remote/path
```

Appliquez la configuration :

```bash
mutagen project start
```

---

## Bonnes pratiques

1. **Exclure les fichiers inutiles** : Utilisez des règles d'exclusion pour éviter de synchroniser des fichiers temporaires ou volumineux (ex. `node_modules`, `.git`).
2. **Utiliser le mode `two-way-resolved`** : Ce mode permet de résoudre automatiquement les conflits entre les fichiers locaux et distants.
3. **Surveiller les performances** : Vérifiez régulièrement l'état des sessions avec `mutagen sync list`.

---

## Liens utiles

- [Documentation officielle Mutagen](https://mutagen.io/documentation)
- [Tutoriels Mutagen](https://mutagen.io/tutorials)
- [Exemples de configuration Mutagen](https://github.com/mutagen-io/mutagen)
