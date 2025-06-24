# 📦 Nginx

## Introduction

Nginx est un serveur web performant utilisé pour le reverse proxy, la gestion des connexions, et le load balancing. Il est largement adopté pour sa capacité à gérer un grand nombre de connexions simultanées avec une faible utilisation des ressources.

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

---

## Bonnes pratiques

1. **Utiliser des fichiers de configuration séparés** : Divisez les configurations en fichiers dans `/etc/nginx/sites-available/` et activez-les avec des liens symboliques dans `/etc/nginx/sites-enabled/`.
2. **Activer la compression** : Utilisez `gzip` pour réduire la taille des réponses HTTP.

   ```nginx
   gzip on;
   gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;
   ```

3. **Surveiller les logs** : Analysez les fichiers de logs pour identifier les problèmes et optimiser les performances.

---

## Liens utiles

- [Documentation officielle Nginx](https://nginx.org/en/docs/)
- [Tutoriels Nginx](https://www.digitalocean.com/community/tutorials/tag/nginx)
- [Exemples de configuration Nginx](https://github.com/nginx/nginx/tree/main/conf)
