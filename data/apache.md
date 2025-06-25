# 📦 Apache

## Introduction

Apache HTTP Server est un serveur web open-source utilisé pour héberger des sites web, servir des fichiers statiques, et gérer des applications dynamiques. Il est largement utilisé pour sa flexibilité et ses modules extensibles.

---

## Commandes essentielles

### Gestion du service Apache

```bash
sudo systemctl start apache2    # Démarre le serveur Apache
sudo systemctl stop apache2     # Arrête le serveur Apache
sudo systemctl restart apache2  # Redémarre le serveur Apache
sudo systemctl reload apache2   # Recharge la configuration sans arrêter le service
sudo systemctl status apache2   # Vérifie l'état du serveur Apache
```

### Test et validation de configuration

```bash
sudo apachectl configtest        # Teste la configuration Apache
sudo apachectl graceful          # Recharge la configuration sans interrompre les connexions
```

---

## Configuration des fichiers

Les fichiers de configuration Apache sont généralement situés dans `/etc/apache2/`.

- **Modifier la configuration principale** :

  ```bash
  sudo nano /etc/apache2/apache2.conf
  ```

- **Activer un site** :

  ```bash
  sudo a2ensite my-site.conf
  sudo systemctl reload apache2
  ```

- **Désactiver un site** :

  ```bash
  sudo a2dissite my-site.conf
  sudo systemctl reload apache2
  ```

---

## Modules Apache

Apache prend en charge des modules pour étendre ses fonctionnalités.

### Modules courants

- **mod_rewrite** : Permet de réécrire les URL.
- **mod_ssl** : Ajoute le support HTTPS.
- **mod_proxy** : Implémente un reverse proxy.
- **mod_headers** : Permet de modifier les en-têtes HTTP.
- **mod_deflate** : Active la compression des réponses HTTP.

### Activer ou désactiver un module

```bash
sudo a2enmod rewrite              # Active un module
sudo a2dismod rewrite             # Désactive un module
sudo systemctl restart apache2    # Redémarre Apache pour appliquer les modifications
```

---

## Exemples pratiques

### Configuration d'un Virtual Host

Un Virtual Host permet d'héberger plusieurs sites sur un même serveur.

```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/example
    <Directory /var/www/example>
        AllowOverride All
        Require all granted
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/example-error.log
    CustomLog ${APACHE_LOG_DIR}/example-access.log combined
</VirtualHost>
```

### Redirection HTTP vers HTTPS

Ajoutez cette configuration pour forcer les connexions HTTPS.

```apache
<VirtualHost *:80>
    ServerName example.com
    Redirect permanent / https://example.com/
</VirtualHost>
```

### Configuration de reverse proxy

Utilisez Apache comme reverse proxy pour rediriger les requêtes vers un serveur backend.

```apache
<VirtualHost *:80>
    ServerName api.example.com

    ProxyPreserveHost On
    ProxyPass / http://localhost:3000/
    ProxyPassReverse / http://localhost:3000/
</VirtualHost>
```

### Compression des réponses HTTP

Activez la compression pour réduire la taille des réponses.

```apache
<IfModule mod_deflate.c>
    AddOutputFilterByType DEFLATE text/html text/plain text/xml application/json
</IfModule>
```

---

## Bonnes pratiques

1. **Utiliser des fichiers de configuration séparés** : Divisez les configurations en fichiers dans `/etc/apache2/sites-available/` et activez-les avec des liens symboliques dans `/etc/apache2/sites-enabled/`.
2. **Activer la compression** : Utilisez `mod_deflate` pour réduire la taille des réponses HTTP.
3. **Sécuriser les connexions** : Configurez HTTPS avec `mod_ssl` et obtenez des certificats SSL gratuits via Let's Encrypt.
4. **Surveiller les logs** : Analysez les fichiers de logs pour identifier les problèmes et optimiser les performances.
5. **Limiter les accès** : Utilisez des directives comme `Require` pour restreindre l'accès à certaines ressources.

---

## Liens utiles

- [Documentation officielle Apache](https://httpd.apache.org/docs/)
- [Guide de configuration Virtual Hosts](https://httpd.apache.org/docs/current/vhosts/)
- [Modules Apache](https://httpd.apache.org/docs/current/mod/)
