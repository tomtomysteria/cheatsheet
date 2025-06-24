# 📦 Spring Boot

## Introduction

Spring Boot est un framework Java basé sur Spring qui simplifie la création d'applications autonomes et prêtes pour la production. Il offre une configuration minimale et des fonctionnalités intégrées comme le serveur web embarqué.

---

## Commandes essentielles

### Gestion des projets

```bash
mvn spring-boot:run                  # Démarre l'application Spring Boot
mvn clean install                    # Compile et installe le projet
mvn package                          # Crée un fichier JAR ou WAR
java -jar target/my-app.jar          # Exécute l'application packagée
```

### Initialisation de projet

```bash
spring init --dependencies=web,data-jpa mysql my-app  # Crée un projet Spring Boot avec des dépendances
```

---

## Exemples pratiques

### Exemple de contrôleur REST

```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {
    @GetMapping("/")
    public String hello() {
        return "Hello, Spring Boot!";
    }
}
```

### Configuration de la base de données

Ajoutez les paramètres de connexion dans `application.properties` :

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=password
spring.jpa.hibernate.ddl-auto=update
```

### Utilisation de JPA pour les entités

```java
import jakarta.persistence.Entity;
import jakarta.persistence.Id;

@Entity
public class User {
    @Id
    private Long id;
    private String name;
    private String email;

    // Getters et setters
}
```

### Exemple de repository

```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<User, Long> {
}
```

---

## Bonnes pratiques

1. **Utiliser des profils Spring** : Configurez des profils pour gérer différents environnements (ex. développement, production).

   ```properties
   spring.profiles.active=dev
   ```

2. **Activer les logs** : Configurez les logs pour surveiller les performances et les erreurs.

   ```properties
   logging.level.org.springframework=DEBUG
   ```

3. **Utiliser des tests automatisés** : Implémentez des tests unitaires et d'intégration avec JUnit et MockMvc.

---

## Liens utiles

- [Documentation officielle Spring Boot](https://spring.io/projects/spring-boot)
- [Tutoriels Spring Boot](https://spring.io/guides)
- [Exemples de projets Spring Boot](https://github.com/spring-projects/spring-boot/tree/main/spring-boot-samples)
