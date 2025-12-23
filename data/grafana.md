# 📦 Grafana

## Introduction

Grafana est un outil de **visualisation** et d’**alerting**. Il se connecte à des sources de données (Prometheus, Elasticsearch, Loki, PostgreSQL, …) pour construire des dashboards.

---

## Concepts clés

### Data sources

- Prometheus (métriques)
- Elasticsearch (logs/événements)
- PostgreSQL (requêtes)

### Dashboards

- Panels (graph, table, stat…)
- Variables (filtres : env, instance, service)
- Alerting sur panels

### Provisioning

Possibilité de provisionner datasources/dashboards par fichiers YAML (pratique en GitOps).

---

## Démarrage rapide (Docker)

```bash
docker run -d --name grafana -p 3000:3000 grafana/grafana:latest
```

Par défaut :

- URL : `http://localhost:3000`
- login : `admin` / `admin`

---

## Exemple : brancher Prometheus

1. Dans Grafana → **Connections** → **Data sources** → **Add data source**.
2. Choisir Prometheus.
3. URL : `http://prometheus:9090` (ou votre endpoint).

---

## Bonnes pratiques

### À connaître en production

### Alerting

Grafana peut déclencher des alertes (emails, Slack, webhook…). Le piège courant : alerter sur “CPU haut” plutôt que sur des symptômes (latence/erreurs).

### Provisioning (GitOps)

Souvent on provisionne datasources/dashboards via fichiers (GitOps) pour éviter les configs manuelles.

1. **Variables** : standardiser `env`, `service`, `instance`.
2. **Dashboards par domaine** : infra / app / DB.
3. **Alertes** : sur symptôme utilisateur (latence/erreurs), pas uniquement sur ressources.
4. **Provisioning** : garder dashboards en Git quand possible.

---

## Liens utiles

- [Grafana docs](https://grafana.com/docs/grafana/latest/)
- [Dashboards community](https://grafana.com/grafana/dashboards/)
