# 📦 Prometheus

## Introduction

Prometheus est un système de **monitoring orienté métriques**. Il collecte des métriques via **scraping HTTP** (pull) et permet de requêter via **PromQL**. Il est souvent couplé à Grafana pour la visualisation et à Alertmanager pour les alertes.

---

## Concepts clés

### Scrape

Prometheus interroge périodiquement des endpoints `/metrics` (exporters).

### Exporters

- Node Exporter (OS)
- cAdvisor/kube-state-metrics (Kubernetes)
- Applications (ex: Spring Boot Actuator)

### Types de métriques

- counter
- gauge
- histogram
- summary

---

## Exemple `prometheus.yml`

```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'springboot'
    metrics_path: /actuator/prometheus
    static_configs:
      - targets: ['host.docker.internal:8080']
```

---

## PromQL (rappels)

- Taux par seconde :

```promql
rate(http_server_requests_seconds_count[5m])
```

- Moyenne de latence (exemple histogram) :

```promql
histogram_quantile(0.95, sum(rate(http_server_requests_seconds_bucket[5m])) by (le))
```

---

## Spring Boot + Prometheus

Souvent via :

- `spring-boot-starter-actuator`
- `micrometer-registry-prometheus`

Endpoint typique :

- `/actuator/prometheus`

---

## Bonnes pratiques

## À connaître en production

### Cardinalité des labels

Éviter des labels avec valeurs très variées (ex: `userId`, `requestId`) → explosion mémoire/stockage.

### Recording rules / alerting

- recording rules : pré-calcul pour dashboards
- alerting : Alertmanager ou Grafana (selon stack)

1. **Labels maîtrisés** : éviter une cardinalité explosive.
2. **Dashboards** : partir des métriques RED/USE (latence/erreurs/saturation).
3. **Alertes** : basées sur des SLO (pas sur “CPU à 90%” uniquement).
4. **Rétention** : dimensionner stockage + règles.

---

## Liens utiles

- [Prometheus](https://prometheus.io/docs/)
- [PromQL](https://prometheus.io/docs/prometheus/latest/querying/basics/)
