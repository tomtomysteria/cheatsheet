# 📦 RabbitMQ

## Introduction

RabbitMQ est un **message broker** (AMQP) orienté files/queues. Il est très utilisé pour :

- communication asynchrone entre services
- jobs/background processing
- intégration (pub/sub via exchanges)

---

## Concepts clés

### Producer / consumer

- **producer** publie un message.
- **consumer** consomme un message depuis une queue.

### Exchange / queue / binding

- **exchange** : reçoit les messages et les route.
- **queue** : stocke les messages.
- **binding** : règle de routage entre exchange et queue.

Types d’exchanges :

- `direct` : routage exact (routing key)
- `topic` : routage par pattern (`orders.*`)
- `fanout` : broadcast

### Ack / prefetch

- `ack` : accusé de traitement.
- `prefetch` : limite de messages non-ack par consumer.

### DLQ (Dead Letter Queue)

Permet de rediriger les messages rejetés/expirés.

---

## Commandes essentielles

Gestion du serveur :

```bash
rabbitmqctl status
rabbitmqctl list_queues
rabbitmqctl list_exchanges
rabbitmqctl list_bindings
```

Activer l’UI (si installé) :

```bash
rabbitmq-plugins enable rabbitmq_management
```

---

## Patterns courants

### Work queue (tâches)

- une queue
- plusieurs consumers
- `prefetch` + `ack` pour backpressure

### Pub/Sub

- exchange `fanout` ou `topic`
- une queue par consumer (ou par service)

---

## Bonnes pratiques

## À connaître en poste

### Durabilité

- queues/exchanges **durables**
- messages **persistent** si tu veux survivre à un restart (selon contraintes)

### TTL / DLX

- TTL (expiration) + Dead Letter Exchange (DLX) pour construire une stratégie retry/DLQ.

### Quorum queues

Souvent recommandées pour une meilleure fiabilité (vs classic queues) en cluster.

1. **Toujours ack** après traitement réussi.
2. **Retry/DLQ** : prévoir une stratégie d’échec.
3. **Limiter la taille** des messages (mettre payload gros en stockage et envoyer une référence).
4. **Configurer `prefetch`** pour éviter de saturer un consumer.
5. **Monitoring** : queue depth, rate, consumers.

---

## Liens utiles

- [RabbitMQ docs](https://www.rabbitmq.com/documentation.html)
- [AMQP concepts](https://www.rabbitmq.com/tutorials/amqp-concepts.html)
