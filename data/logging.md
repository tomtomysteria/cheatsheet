# 📜 Logs et Niveaux de Logs

## Introduction

Les logs sont des enregistrements d'événements ou d'activités générés par une application ou un système. Ils sont essentiels pour le suivi, le débogage et la maintenance des applications.

---

## Pourquoi utiliser les logs ?

1. **Débogage** : Identifier et résoudre les problèmes dans le code.
2. **Audit** : Suivre les actions des utilisateurs et des systèmes.
3. **Monitoring** : Surveiller les performances et la santé des applications.
4. **Sécurité** : Détecter les activités suspectes ou malveillantes.

---

## Niveaux de Logs

Les niveaux de logs permettent de catégoriser les messages en fonction de leur importance ou de leur gravité.

### 1. **TRACE**

- Niveau le plus détaillé.

- Utilisé pour suivre l'exécution du code ligne par ligne.

- Exemple : "Entrée dans la méthode X avec les paramètres Y."

### 2. **DEBUG**

- Utilisé pour le débogage.

- Fournit des informations utiles pour les développeurs.

- Exemple : "Valeur de la variable Z après calcul."

### 3. **INFO**

- Utilisé pour des informations générales sur le fonctionnement de l'application.

- Exemple : "L'application a démarré avec succès."

### 4. **WARN**

- Indique des situations potentiellement problématiques.

- Exemple : "Connexion lente à la base de données."

### 5. **ERROR**

- Indique des erreurs qui empêchent le fonctionnement normal de l'application.

- Exemple : "Échec de la requête à l'API externe."

### 6. **FATAL**

- Indique des erreurs critiques qui nécessitent une intervention immédiate.

- Exemple : "Impossible de démarrer le serveur."

---

## Bonnes pratiques pour les logs

1. **Utiliser des niveaux appropriés** : Choisir le niveau de log adapté à chaque message.
2. **Éviter les informations sensibles** : Ne pas inclure de mots de passe ou de données personnelles dans les logs.
3. **Structurer les logs** : Utiliser des formats comme JSON pour faciliter l'analyse.
4. **Configurer la rotation des logs** : Éviter que les fichiers de logs ne deviennent trop volumineux.
5. **Surveiller les logs** : Utiliser des outils comme ELK (Elasticsearch, Logstash, Kibana) pour analyser les logs.

Voir aussi : `data/elk.md`

---

## Logs structurés (JSON)

Les logs structurés facilitent la recherche et les dashboards (ELK). Recommandations :

- Logguer au format JSON
- Ajouter des champs standard : `service`, `env`, `traceId`/`spanId` (si tracing), `requestId`
- Ne pas logguer de données sensibles (PII, secrets)

---

## Outils de gestion des logs

1. **Log4j** (Java) : Framework populaire pour la gestion des logs.
2. **Winston** (Node.js) : Bibliothèque flexible pour les logs.
3. **Python Logging** : Module intégré pour gérer les logs.
4. **ELK Stack** : Suite d'outils pour la collecte, l'analyse et la visualisation des logs.

---

## Exemple de configuration

### Log4j (Java)

```xml
<Configuration status="WARN">
  <Appenders>
    <Console name="Console" target="SYSTEM_OUT">
      <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss} [%t] %-5level %logger{36} - %msg%n" />
    </Console>
  </Appenders>
  <Loggers>
    <Root level="info">
      <AppenderRef ref="Console" />
    </Root>
  </Loggers>
</Configuration>
```

### Winston (Node.js)

```javascript
const winston = require('winston');

const logger = winston.createLogger({
  level: 'info',
  format: winston.format.json(),
  transports: [
    new winston.transports.Console(),
    new winston.transports.File({ filename: 'error.log', level: 'error' }),
    new winston.transports.File({ filename: 'combined.log' }),
  ],
});

logger.info('Application démarrée');
logger.error('Erreur critique détectée');
```

---

## Liens utiles

- [Documentation Log4j](https://logging.apache.org/log4j/2.x/)
- [Documentation Winston](https://github.com/winstonjs/winston)
- [Tutoriels sur les logs](https://www.tutorialspoint.com/logging/index.htm)
