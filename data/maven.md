# 📦 Maven

## Introduction

Maven est un outil de gestion de projet et de construction pour Java. Il simplifie la gestion des dépendances, la compilation, les tests, et le déploiement des projets Java grâce à un fichier de configuration centralisé (`pom.xml`). Maven est basé sur le concept de "Convention over Configuration", ce qui réduit la complexité de la configuration des projets.

---

## Concepts clés

### Pourquoi utiliser Maven ?

1. **Gestion des dépendances** : Maven automatise le téléchargement et la gestion des bibliothèques nécessaires à un projet.
2. **Standardisation** : Maven impose une structure de projet standardisée, facilitant la collaboration entre les développeurs.
3. **Automatisation** : Maven permet d'automatiser les étapes de construction, de test, et de déploiement.
4. **Extensibilité** : Maven prend en charge une large gamme de plugins pour ajouter des fonctionnalités supplémentaires.

### Enjeux pour les développeurs

1. **Gestion des conflits de dépendances** : Maven résout automatiquement les conflits de versions, mais cela peut nécessiter une analyse approfondie.
2. **Performance** : Optimisez les builds en configurant correctement les plugins et en utilisant le cache local.
3. **Portabilité** : Maven garantit que les builds sont reproductibles sur différents environnements grâce au fichier `pom.xml`.

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
mvn site                       # Génère un site de documentation pour le projet
```

### Gestion des dépendances

```bash
mvn dependency:tree            # Affiche l'arborescence des dépendances
mvn dependency:analyze         # Analyse les dépendances inutilisées ou manquantes
mvn dependency:resolve         # Résout les dépendances du projet
```

### Gestion des plugins

```bash
mvn help:describe -Dplugin=<plugin-name>  # Affiche les détails d'un plugin
mvn exec:java -Dexec.mainClass=<main-class>  # Exécute une classe Java
mvn versions:display-dependency-updates  # Affiche les mises à jour disponibles pour les dépendances
```

### Gestion des profils

```bash
mvn clean install -Pdev           # Exécute Maven avec un profil spécifique
mvn help:active-profiles          # Affiche les profils actifs
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
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>11</source>
                    <target>11</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
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

### Utiliser un profil Maven

```xml
<profiles>
    <profile>
        <id>dev</id>
        <properties>
            <env>development</env>
        </properties>
    </profile>
    <profile>
        <id>prod</id>
        <properties>
            <env>production</env>
        </properties>
    </profile>
</profiles>
```

---

## Bonnes pratiques

## À connaître en entreprise

### Multi-modules

Souvent un parent `pom` + plusieurs modules (`api`, `service`, `web`, etc.).

### BOM / dependencyManagement

Centraliser les versions dans `<dependencyManagement>` (ou utiliser un BOM) pour éviter les conflits.

### Maven Wrapper

Préférer `./mvnw` (version Maven contrôlée) dans les pipelines.

### `settings.xml`

Utile en entreprise (proxy, mirror, registry interne) : dépôt Nexus/Artifactory.

1. **Versionner le fichier `pom.xml`** : Ajoutez `pom.xml` au contrôle de version pour garantir la cohérence des dépendances.
2. **Utiliser des profils Maven** : Configurez des profils pour gérer différents environnements (ex. développement, production).
3. **Analyser les dépendances** : Utilisez `mvn dependency:analyze` pour identifier les dépendances inutilisées.
4. **Configurer les plugins** : Ajoutez des plugins comme `maven-compiler-plugin` pour gérer la compilation.
5. **Automatiser les builds** : Intégrez Maven dans les pipelines CI/CD pour automatiser les tests et les déploiements.

---

## Outils utiles

- **Maven Wrapper** : Simplifie l'exécution de Maven sans nécessiter une installation locale.
- **Nexus/Artifactory** : Dépôts pour gérer les dépendances Maven.
- **Jenkins** : Intégration de Maven dans les pipelines CI/CD.
- **SonarQube** : Analyse de la qualité du code dans les projets Maven.

---

## Commandes avancées

### Analyse des performances

```bash
mvn dependency:analyze-only         # Analyse uniquement les dépendances
mvn dependency:purge-local-repository # Purge les dépendances du dépôt local
```

### Gestion des versions

```bash
mvn versions:set -DnewVersion=2.0.0 # Change la version du projet
mvn versions:commit                 # Valide les modifications de version
mvn versions:rollback               # Annule les modifications de version
```

### Génération de documentation

```bash
mvn site                            # Génère un site de documentation pour le projet
mvn site:deploy                     # Déploie le site de documentation
```

---

## Liens utiles

- [Documentation officielle Maven](https://maven.apache.org/)
- [Guide Maven](https://maven.apache.org/guides/)
- [Exemples Maven](https://github.com/apache/maven-examples)
- [SonarQube](https://www.sonarqube.org/)
