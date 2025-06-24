# 📦 Maven

## Introduction

Maven est un outil de gestion de projet et de construction pour Java. Il simplifie la gestion des dépendances, la compilation, les tests, et le déploiement des projets Java grâce à un fichier de configuration centralisé (`pom.xml`).

---

## Commandes essentielles

### Construction et gestion de projet

```bash
mvn clean                      # Nettoie les fichiers générés
mvn compile                    # Compile le code source
mvn test                       # Exécute les tests
mvn package                    # Crée un fichier JAR ou WAR
mvn install                    # Installe le projet dans le dépôt local
mvn deploy                     # Déploie le projet dans un dépôt distant
```

### Gestion des dépendances

```bash
mvn dependency:tree            # Affiche l'arborescence des dépendances
mvn dependency:analyze         # Analyse les dépendances inutilisées ou manquantes
```

### Gestion des plugins

```bash
mvn help:describe -Dplugin=<plugin-name>  # Affiche les détails d'un plugin
mvn exec:java -Dexec.mainClass=<main-class>  # Exécute une classe Java
```

---

## Exemples pratiques

### Exemple de fichier `pom.xml`

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>my-app</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-core</artifactId>
            <version>5.3.20</version>
        </dependency>
    </dependencies>
</project>
```

### Ajouter une dépendance

Ajoutez une dépendance directement dans le fichier `pom.xml` :

```xml
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
    <version>3.12.0</version>
</dependency>
```

### Exécuter une classe principale

```bash
mvn exec:java -Dexec.mainClass=com.example.Main
```

---

## Bonnes pratiques

1. **Versionner le fichier `pom.xml`** : Ajoutez `pom.xml` au contrôle de version pour garantir la cohérence des dépendances.
2. **Utiliser des profils Maven** : Configurez des profils pour gérer différents environnements (ex. développement, production).

   ```xml
   <profiles>
       <profile>
           <id>dev</id>
           <properties>
               <env>development</env>
           </properties>
       </profile>
   </profiles>
   ```

3. **Analyser les dépendances** : Utilisez `mvn dependency:analyze` pour identifier les dépendances inutilisées.

---

## Liens utiles

- [Documentation officielle Maven](https://maven.apache.org/)
- [Guide Maven](https://maven.apache.org/guides/)
- [Exemples Maven](https://github.com/apache/maven-examples)
