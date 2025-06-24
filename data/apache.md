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
sudo systemctl status apache2   # Vérifie l'état du serveur Apache
```

### Configuration des fichiers

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

### Modules Apache

Apache prend en charge des modules pour étendre ses fonctionnalités.

- **Activer un module** :

  ```bash
  sudo a2enmod rewrite
  sudo systemctl restart apache2
  ```

- **Désactiver un module** :

  ```bash
  sudo a2dismod rewrite
  sudo systemctl restart apache2
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

---

## Liens utiles

- [Documentation officielle Apache](https://httpd.apache.org/docs/)
- [Guide de configuration Virtual Hosts](https://httpd.apache.org/docs/current/vhosts/)
- [Modules Apache](https://httpd.apache.org/docs/current/mod/)
