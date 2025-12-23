# 📦 ELK (Elasticsearch / Logstash / Kibana)

## Introduction

ELK désigne une stack pour la **centralisation et l’analyse de logs** :

- **Elasticsearch** : stockage + indexation + recherche
- **Logstash** : ingestion/parse/transformation (optionnel)
- **Kibana** : exploration et dashboards

Souvent on ajoute **Beats** (ex: Filebeat) pour expédier les logs.

---

## Concepts clés

### Index / document

- Un **document** (JSON) est stocké dans un **index**.
- Un index est souvent découpé dans le temps (ex: `logs-2025.12.23`).

### Pipeline d’ingestion

Sources possibles :

- fichiers logs → Filebeat → Elasticsearch
- app → JSON logs → Logstash → Elasticsearch

### Recherche

- Kibana (Discover)
- Query DSL / KQL

---

## Bonnes pratiques côté application (Spring Boot)

1. **Logs structurés JSON** (plutôt que texte libre).
2. Inclure des champs : `service`, `env`, `traceId`, `spanId`, `userId` (si pertinent).
3. Éviter les données sensibles (PII) dans les logs.

---

## Démarrage rapide (Docker Compose – exemple)

```yaml
version: '3.8'
services:
  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:8.15.3
    environment:
      - discovery.type=single-node
      - xpack.security.enabled=false
    ports:
      - "9200:9200"

  kibana:
    image: docker.elastic.co/kibana/kibana:8.15.3
    environment:
      - ELASTICSEARCH_HOSTS=http://elasticsearch:9200
    ports:
      - "5601:5601"
    depends_on:
      - elasticsearch
```

---

## Requêtes utiles

### Tester Elasticsearch

```bash
curl http://localhost:9200
```

### Lister les index

```bash
curl "http://localhost:9200/_cat/indices?v"
```

---

## Bonnes pratiques

## À connaître en production

### Ingestion

Choix courant : Filebeat → Elasticsearch (simple) ou Filebeat → Logstash → Elasticsearch (si parsing/transformation avancés).

### ILM / rétention

Définir une politique de rétention (temps/taille) pour maîtriser les coûts.

1. **Rotation / ILM** : gérer la rétention (par taille/temps).
2. **Mapping** : contrôler les types (dates, keywords) pour éviter les surprises.
3. **Sécurité** : auth/TLS en production.
4. **Coûts** : les logs coûtent cher → filtrer, échantillonner, rétention adaptée.

---

## Liens utiles

- [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html)
- [Kibana](https://www.elastic.co/guide/en/kibana/current/index.html)
- [Filebeat](https://www.elastic.co/guide/en/beats/filebeat/current/index.html)
