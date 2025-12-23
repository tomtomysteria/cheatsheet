# 📦 Kafka

## Introduction

Apache Kafka est une plateforme de **streaming d’événements**. Elle permet de publier/consommer des messages à haut débit via des **topics** partitionnés.

Cas d’usage :

- Event-driven architecture
- Audit log / event sourcing
- Ingestion temps réel (metrics, logs)

---

## Concepts clés

### Broker / cluster

- **broker** : un nœud Kafka.
- **cluster** : ensemble de brokers.

### Topic / partition

- **topic** : catégorie de messages.
- **partition** : sous-ensemble ordonné du topic.
- Le parallélisme vient des partitions.

### Producer / consumer

- **producer** publie des messages.
- **consumer** lit des messages.

### Consumer group

- Plusieurs consommateurs dans un même groupe se répartissent les partitions.
- Chaque groupe maintient des **offsets** (position de lecture).

### Livraison

- souvent **at-least-once** (le plus courant)
- possible **exactly-once** mais plus complexe

---

## Commandes essentielles (kafka-* tools)

> Les commandes dépendent de la distribution Kafka installée.

Lister/créer un topic :

```bash
kafka-topics --bootstrap-server localhost:9092 --list

kafka-topics --bootstrap-server localhost:9092 \
  --create --topic orders \
  --partitions 3 --replication-factor 1
```

Produire / consommer :

```bash
kafka-console-producer --bootstrap-server localhost:9092 --topic orders

kafka-console-consumer --bootstrap-server localhost:9092 --topic orders --from-beginning
```

Décrire un topic :

```bash
kafka-topics --bootstrap-server localhost:9092 --describe --topic orders
```

---

## Bonnes pratiques

## À connaître en poste

### Offsets / commits

- Un consumer avance via des **offsets**.
- Les commits (auto ou manuels) conditionnent la reprise et les “doublons” (at-least-once).

### Rétention vs compaction

- **retention** : purge par temps/taille
- **compaction** : garde la dernière valeur par clé

### Retry / DLQ

Pattern courant : retry topic(s) + DLQ pour isoler les messages invalides.

1. **Définir un partitionnement** cohérent (clé de partition) pour garantir l’ordre par entité.
2. **Surveiller la rétention** (temps/taille) et la croissance des topics.
3. **Gérer les schémas** (JSON/Avro/Protobuf) : éviter les breaking changes.
4. **Idempotence côté consumer** : gérer les retries (at-least-once).
5. **DLQ / retry topics** : prévoir les messages invalides.

---

## Liens utiles

- [Kafka](https://kafka.apache.org/documentation/)
- [Confluent (guides pratiques)](https://docs.confluent.io/)
