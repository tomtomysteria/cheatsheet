# 📦 Spring Boot

## Introduction

Spring Boot est un framework Java basé sur Spring qui simplifie la création d'applications autonomes et prêtes pour la production. Il offre une configuration minimale, un serveur web embarqué, et une intégration facile avec des bases de données, des services cloud, et des outils de monitoring. Spring Boot est idéal pour développer des API REST, des microservices, et des applications web complexes.

---

## Commandes essentielles

### Maven CLI

```bash
mvn spring-boot:run                  # Démarre l'application Spring Boot
mvn clean install                    # Compile et installe le projet
mvn package                          # Crée un fichier JAR ou WAR
mvn dependency:tree                  # Affiche l'arborescence des dépendances
mvn test                             # Exécute les tests
mvn spring-boot:build-image          # Crée une image Docker pour l'application
java -jar target/my-app.jar          # Exécute l'application packagée
```

### Initialisation de projet

```bash
spring init --dependencies=web,data-jpa mysql my-app  # Crée un projet Spring Boot avec des dépendances
```

---

## Concepts clés

### Exemple de contrôleur REST

```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {
    @GetMapping("/api/hello")
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

### Exemple de modèle (DTO)

```java
public class UserDTO {
    private Long id;
    private String name;
    private String email;

    // Getters et setters
}
```

### Exemple d'entité avec JPA

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

### Exemple de repository avec Spring Data JPA

```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<User, Long> {
}
```

### Exemple de service

```java
import org.springframework.stereotype.Service;

@Service
public class UserService {
    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    public User getUserById(Long id) {
        return userRepository.findById(id).orElse(null);
    }
}
```

### Injection de dépendances

Ajoutez le service dans le contrôleur :

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class UserController {
    @Autowired
    private UserService userService;

    @GetMapping("/api/user")
    public User getUser() {
        return userService.getUserById(1L);
    }
}
```

---

## Gestion des logs

Ajoutez les logs dans `application.properties` :

```properties
logging.level.org.springframework=DEBUG
logging.file.name=logs/springboot.log
```

Exemple d'utilisation des logs dans un service :

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Service;

@Service
public class LoggingService {
    private static final Logger logger = LoggerFactory.getLogger(LoggingService.class);

    public void logMessage(String message) {
        logger.info("Message reçu : {}", message);
    }

    public void logError(String error) {
        logger.error("Erreur : {}", error);
    }
}
```

---

## Tests avec Spring Boot

### Utilisation de JUnit et MockMvc

Ajoutez les dépendances dans `pom.xml` :

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```

Exemple de test de contrôleur :

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.AutoConfigureMockMvc;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.web.servlet.MockMvc;

import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;

@SpringBootTest
@AutoConfigureMockMvc
public class HelloControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @Test
    public void testHelloEndpoint() throws Exception {
        mockMvc.perform(get("/api/hello"))
               .andExpect(status().isOk());
    }
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

3. **Structurer les projets** : Organisez les projets en couches (ex. contrôleurs, services, modèles, DTOs, entités) pour améliorer la maintenabilité.
4. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
5. **Utiliser Actuator** : Intégrez Actuator pour surveiller l'état de l'application et exposer des métriques.
6. **Sécuriser les endpoints** : Implémentez Spring Security pour protéger les endpoints sensibles.
7. **Configurer les environnements** : Utilisez des fichiers `.env` ou `application.properties` pour gérer les configurations.

---

## Liens utiles

- [Documentation officielle Spring Boot](https://spring.io/projects/spring-boot)
- [Tutoriels Spring Boot](https://spring.io/guides)
- [Exemples de projets Spring Boot](https://github.com/spring-projects/spring-boot/tree/main/spring-boot-samples)
- [Documentation Spring Security](https://spring.io/projects/spring-security)
- [Documentation Spring Data JPA](https://spring.io/projects/spring-data-jpa)
