# 📦 Linux

## Introduction

Linux est un système d'exploitation open-source basé sur le noyau Linux. Il est utilisé dans une variété de contextes, allant des serveurs aux ordinateurs personnels, en passant par les systèmes embarqués. Sa flexibilité, sa sécurité et sa robustesse en font un choix populaire pour les développeurs et les administrateurs système.

---

## Concepts clés

### Pourquoi utiliser Linux ?

1. **Open-source** : Linux est gratuit et son code source est accessible, permettant une personnalisation complète.
2. **Sécurité** : Linux est réputé pour sa sécurité grâce à sa gestion des permissions et son architecture robuste.
3. **Stabilité** : Idéal pour les serveurs et les environnements critiques grâce à sa fiabilité.
4. **Flexibilité** : Linux peut être utilisé sur des serveurs, des ordinateurs personnels, des systèmes embarqués, et même des superordinateurs.

### Enjeux pour les développeurs

1. **Automatisation** : Linux offre des outils puissants comme Bash et Cron pour automatiser les tâches.
2. **Performance** : Optimisez les ressources système avec des commandes avancées et des outils de surveillance.
3. **Interopérabilité** : Linux est compatible avec de nombreux langages de programmation et frameworks.
4. **Sécurité** : Implémentez des mécanismes comme SSH, pare-feu, et permissions pour protéger vos systèmes.

---

## Commandes essentielles

### Gestion des fichiers et répertoires

```bash
ls                                  # Liste les fichiers et répertoires
cd <directory>                      # Change de répertoire
pwd                                 # Affiche le chemin du répertoire courant
mkdir <directory>                   # Crée un nouveau répertoire
rm <file>                           # Supprime un fichier
rm -r <directory>                   # Supprime un répertoire et son contenu
cp <source> <destination>           # Copie un fichier ou un répertoire
mv <source> <destination>           # Déplace ou renomme un fichier ou répertoire
touch <file>                        # Crée un fichier vide
stat <file>                         # Affiche les informations détaillées sur un fichier
tree                                # Affiche la structure des répertoires sous forme d'arborescence
```

### Gestion des processus

```bash
ps                                 # Liste les processus en cours
top                                # Affiche les processus en temps réel
htop                               # Alternative interactive à `top`
kill <PID>                         # Termine un processus par son ID
killall <process_name>             # Termine tous les processus avec le nom donné
jobs                               # Liste les processus en arrière-plan
fg <job_id>                        # Ramène un processus en arrière-plan au premier plan
bg <job_id>                        # Reprend un processus en arrière-plan
```

### Gestion des permissions

```bash
chmod <permissions> <file>         # Change les permissions d'un fichier
chown <user>:<group> <file>        # Change le propriétaire d'un fichier
umask                              # Affiche ou modifie le masque de permissions par défaut
```

### Réseau

```bash
ping <hostname>                    # Vérifie la connectivité avec un hôte
curl <url>                         # Récupère le contenu d'une URL
wget <url>                         # Télécharge un fichier depuis une URL
scp <source> <user>@<host>:<destination> # Copie des fichiers vers/depuis un serveur distant
netstat -tuln                      # Liste les ports ouverts et les services en écoute
ss -tuln                           # Alternative moderne à netstat
traceroute <hostname>              # Affiche le chemin emprunté par les paquets pour atteindre un hôte
iptables -L                                   # Liste les règles du pare-feu
```

### Gestion des packages (Debian/Ubuntu)

```bash
sudo apt update                    # Met à jour la liste des packages
sudo apt upgrade                   # Met à jour les packages installés
sudo apt install <package>         # Installe un package
sudo apt remove <package>          # Supprime un package
dpkg -l | grep <package_name>      # Vérifie si un package est installé
apt-cache search <keyword>         # Recherche des packages disponibles
sudo apt autoremove                # Supprime les dépendances inutilisées
```

---

## Exemples pratiques

### Recherche de fichiers

```bash
find /path/to/directory -name "filename"  # Recherche un fichier par son nom
find /path/to/directory -type f -mtime -7 # Trouve les fichiers modifiés dans les 7 derniers jours
grep "text" <file>                        # Recherche du texte dans un fichier
grep -r "text" /path/to/directory         # Recherche récursive du texte dans un répertoire
grep -i "text" <file>                     # Recherche insensible à la casse
locate <filename>                         # Recherche rapide de fichiers par leur nom (nécessite une base de données mise à jour)
```

### Compression et décompression

```bash
tar -czvf archive.tar.gz <directory>      # Compresse un répertoire
tar -xzvf archive.tar.gz                  # Décompresse une archive
tar -cvf archive.tar <directory>          # Archive un répertoire sans compression
gzip archive.tar                          # Compresse une archive TAR avec gzip
gzip <file>                               # Compresse un fichier
gunzip <file.gz>                          # Décompresse un fichier compressé avec gzip
zip -r archive.zip <directory>            # Compresse un répertoire en fichier ZIP
unzip archive.zip                         # Décompresse un fichier ZIP
```

### Surveillance des logs

```bash
tail -f <file>                            # Affiche les dernières lignes d'un fichier en temps réel
journalctl -f                             # Surveille les logs système en temps réel
less <file>                               # Affiche le contenu d'un fichier avec navigation
```

---

## Bonnes pratiques

1. **Utiliser des alias** : Créez des alias pour simplifier les commandes répétitives.

   ```bash
   alias ll="ls -la"
   ```

2. **Automatiser avec des scripts** : Utilisez des scripts Bash pour automatiser les tâches courantes.
3. **Surveiller les ressources** : Utilisez `top`, `htop`, ou `vmstat` pour surveiller l'utilisation des ressources.
4. **Sécuriser le système** : Configurez un pare-feu avec `ufw` et appliquez les mises à jour régulièrement.
5. **Créer des sauvegardes** : Avant de modifier des fichiers critiques, utilisez `cp` ou `rsync` pour sauvegarder.

---

## Outils utiles

- **Bash** : Shell par défaut sur la plupart des distributions Linux.
- **Zsh** : Shell avancé avec des fonctionnalités supplémentaires.
- **tmux** : Gestionnaire de sessions terminal.
- **htop** : Alternative interactive à `top` pour surveiller les processus.
- **nano/vim** : Éditeurs de texte en ligne de commande.
- **rsync** : Synchronisation rapide des fichiers et répertoires.
- **tree** : Affiche la structure des répertoires sous forme d'arborescence.

---

## Commandes avancées

### Gestion des fichiers et répertoires

```bash
du -sh <directory>                             # Affiche la taille d'un répertoire
ln -s <target> <link_name>                     # Crée un lien symbolique vers un fichier ou répertoire
rsync -av <source> <destination>               # Synchronise des fichiers ou répertoires
```

### Gestion des processus et ressources

```bash
lsof -i :<port>                                # Liste les processus utilisant un port spécifique
nice -n <priority> <command>                   # Exécute une commande avec une priorité spécifique
iotop                                         # Surveille l'utilisation des entrées/sorties disque
```

### Surveillance et diagnostic

```bash
dmesg | grep <keyword>                    # Affiche les messages du noyau liés à un mot-clé
vmstat 1                                  # Surveille les performances système en temps réel
iostat                                   # Affiche les statistiques d'utilisation des disques
```

### Gestion des utilisateurs et permissions

```bash
whoami                                   # Affiche l'utilisateur courant
id <username>                            # Affiche les informations sur un utilisateur
passwd <username>                        # Change le mot de passe d'un utilisateur
chmod -R 755 <directory>                 # Change les permissions d'un répertoire et de son contenu
```

### Commandes système

```bash
uptime                                   # Affiche le temps de fonctionnement du système
uname -a                                 # Affiche les informations sur le noyau et le système
df -h                                    # Affiche l'espace disque utilisé et disponible
free -h                                  # Affiche l'utilisation de la mémoire
```

### Automatisation et scripts

```bash
crontab -e                                   # Édite les tâches planifiées pour l'utilisateur courant
watch -n <seconds> <command>                 # Exécute une commande périodiquement
```

---

## Liens utiles

- [Guide complet des commandes Linux](https://linuxcommand.org/)
- [Tutoriels sur les commandes avancées](https://www.tecmint.com/linux-command-line-tips/)
- [Documentation officielle Linux](https://www.kernel.org/doc/html/latest/)

```

### Gestion des packages (Debian/Ubuntu)

```bash
dpkg -l | grep <package_name>                # Vérifie si un package est installé
apt-cache search <keyword>                   # Recherche des packages disponibles
```

### Commandes système

```bash
uptime                                       # Affiche le temps de fonctionnement du système
uname -a                                     # Affiche les informations sur le noyau et le système
df -h                                        # Affiche l'espace disque utilisé et disponible
free -h                                      # Affiche l'utilisation de la mémoire
```

---

## Bonnes pratiques pour les commandes avancées

1. **Utiliser des options de simulation** : Avant d'exécuter des commandes destructives comme `rm` ou `rsync`, utilisez des options de simulation (`--dry-run`) pour vérifier leur comportement.
2. **Créer des sauvegardes** : Avant de modifier des fichiers critiques, créez des sauvegardes avec `cp` ou `rsync`.
3. **Documenter les scripts** : Ajoutez des commentaires dans vos scripts Bash pour expliquer leur fonctionnement.
4. **Surveiller les logs** : Utilisez `tail -f` ou `journalctl` pour surveiller les logs en temps réel.

---

## Liens utiles pour les commandes avancées

- [Guide complet des commandes Linux](https://linuxcommand.org/)
- [Tutoriels sur les commandes avancées](https://www.tecmint.com/linux-command-line-tips/)
- [Documentation officielle Linux](https://www.kernel.org/doc/html/latest/)
