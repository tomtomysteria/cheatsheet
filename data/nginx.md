# 📦 Nginx

## Introduction

Nginx est un serveur web performant utilisé pour le reverse proxy, la gestion des connexions, et le load balancing. Il est largement adopté pour sa capacité à gérer un grand nombre de connexions simultanées avec une faible utilisation des ressources. Nginx est également utilisé pour servir des fichiers statiques, gérer des certificats SSL, et optimiser les performances des applications web.

---

## Concepts clés

### Pourquoi utiliser Nginx ?

1. **Performance** : Nginx est conçu pour gérer des milliers de connexions simultanées avec une faible consommation de mémoire.
2. **Flexibilité** : Il peut être utilisé comme serveur web, reverse proxy, ou load balancer.
3. **Sécurité** : Nginx prend en charge HTTPS, les certificats SSL, et les mécanismes de protection contre les attaques courantes (ex. DDoS).
4. **Scalabilité** : Nginx facilite la mise à l'échelle des applications grâce au load balancing et au caching.

### Enjeux pour les développeurs

1. **Optimisation des performances** : Configurez le caching et la compression pour réduire la latence.
2. **Sécurisation des connexions** : Implémentez HTTPS et configurez les certificats SSL.
3. **Gestion des logs** : Analysez les logs pour identifier les problèmes et améliorer les performances.
4. **Flexibilité des configurations** : Utilisez des fichiers de configuration séparés pour gérer plusieurs sites ou applications.

---

## Commandes essentielles

### Gestion du service Nginx

```bash
sudo systemctl start nginx               # Démarre le serveur Nginx
sudo systemctl stop nginx                # Arrête le serveur Nginx
sudo systemctl restart nginx             # Redémarre le serveur Nginx
sudo systemctl reload nginx              # Recharge la configuration sans arrêter le service
sudo systemctl status nginx              # Vérifie l'état du serveur Nginx
```

### Test et validation de configuration

```bash
sudo nginx -t                            # Teste la configuration Nginx
sudo nginx -s reload                     # Recharge la configuration après modification
```

### Gestion des fichiers de configuration

```bash
sudo nano /etc/nginx/nginx.conf          # Édite le fichier de configuration principal
sudo nano /etc/nginx/sites-available/<site> # Édite la configuration d'un site spécifique
sudo ln -s /etc/nginx/sites-available/<site> /etc/nginx/sites-enabled/ # Active un site
sudo rm /etc/nginx/sites-enabled/<site> # Désactive un site
```

---

## Exemples pratiques

### Configuration d'un Virtual Host

Un Virtual Host permet d'héberger plusieurs sites sur un même serveur.

```nginx
server {
    listen 80;
    server_name example.com www.example.com;

    root /var/www/example;
    index index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }

    error_log /var/log/nginx/example-error.log;
    access_log /var/log/nginx/example-access.log;
}
```

### Configuration de reverse proxy

Utilisez Nginx comme reverse proxy pour rediriger les requêtes vers un serveur backend.

```nginx
server {
    listen 80;
    server_name api.example.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

### Redirection HTTP vers HTTPS

Ajoutez cette configuration pour forcer les connexions HTTPS.

```nginx
server {
    listen 80;
    server_name example.com www.example.com;
    return 301 https://$host$request_uri;
}
```

### Configuration de Load Balancing

Distribuez les requêtes entre plusieurs serveurs backend.

```nginx
upstream backend {
    server backend1.example.com;
    server backend2.example.com;
}

server {
    listen 80;
    server_name example.com;

    location / {
        proxy_pass http://backend;
    }
}
```

### Configuration de caching

Activez le caching pour améliorer les performances.

```nginx
server {
    listen 80;
    server_name example.com;

    location / {
        proxy_cache my_cache;
        proxy_cache_valid 200 302 10m;
        proxy_cache_valid 404 1m;
        proxy_pass http://backend;
    }
}
```

---

## Bonnes pratiques

1. **Utiliser des fichiers de configuration séparés** : Divisez les configurations en fichiers dans `/etc/nginx/sites-available/` et activez-les avec des liens symboliques dans `/etc/nginx/sites-enabled/`.
2. **Activer la compression** : Utilisez `gzip` pour réduire la taille des réponses HTTP.

   ```nginx
   gzip on;
   gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;
   ```

3. **Surveiller les logs** : Analysez les fichiers de logs pour identifier les problèmes et optimiser les performances.
4. **Sécuriser les connexions** : Implémentez HTTPS avec des certificats SSL et configurez les en-têtes de sécurité.
5. **Optimiser les performances** : Configurez le caching et le load balancing pour réduire la latence.

---

## Outils utiles

- **Certbot** : Automatisation de la configuration SSL avec Let's Encrypt.
- **Logrotate** : Gestion des fichiers de logs pour éviter qu'ils ne deviennent trop volumineux.
- **Nginx Amplify** : Outil de monitoring pour Nginx.

---

## Commandes avancées

### Surveillance et diagnostic

```bash
sudo tail -f /var/log/nginx/access.log    # Surveille les logs d'accès en temps réel
sudo tail -f /var/log/nginx/error.log     # Surveille les logs d'erreur en temps réel
```

### Gestion des certificats SSL

```bash
sudo certbot --nginx                     # Configure automatiquement SSL avec Let's Encrypt
sudo certbot renew                       # Renouvelle les certificats SSL
```

### Optimisation des performances

```nginx
worker_processes auto;                   # Configure automatiquement le nombre de processus de travail
worker_connections 1024;                 # Définit le nombre maximum de connexions par processus
```

---

## Liens utiles

- [Documentation officielle Nginx](https://nginx.org/en/docs/)
- [Tutoriels Nginx](https://www.digitalocean.com/community/tutorials/tag/nginx)
- [Exemples de configuration Nginx](https://github.com/nginx/nginx/tree/main/conf)
- [Certbot pour SSL](https://certbot.eff.org/)
