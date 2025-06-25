# 📦 Java

## Introduction

Java est un langage de programmation orienté objet, robuste et multiplateforme. Il est utilisé pour développer des applications web, mobiles, de bureau, ainsi que des systèmes embarqués. Grâce à sa machine virtuelle Java (JVM), Java garantit une portabilité élevée et une exécution sécurisée. Il est également largement utilisé pour les API REST, les microservices, et les applications d'entreprise.

---

## Commandes essentielles

### Compilation et exécution

```bash
javac Main.java               # Compile un fichier Java
java Main                     # Exécute un fichier compilé
java -jar MyApp.jar           # Exécute une application Java packagée
```

### Gestion des packages

```bash
javac -d . Main.java          # Compile et place les fichiers dans des packages
java mypackage.Main           # Exécute une classe dans un package
```

### Maven CLI

```bash
mvn compile                         # Compile le projet
mvn test                            # Exécute les tests
mvn package                         # Crée un fichier JAR ou WAR
mvn clean                           # Nettoie les fichiers générés
mvn install                         # Installe le projet dans le dépôt local
mvn dependency:tree                 # Affiche l'arborescence des dépendances
mvn spring-boot:run                 # Démarre une application Spring Boot
```

### Gradle CLI

```bash
gradle build                        # Compile et construit le projet
gradle test                         # Exécute les tests
gradle clean                        # Nettoie les fichiers générés
gradle run                          # Exécute l'application
gradle dependencies                 # Liste les dépendances du projet
```

---

## Concepts clés

### Classes et objets

```java
public class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    public void greet() {
        System.out.println("Hello, " + name + "!");
    }

    public static void main(String[] args) {
        Person person = new Person("Alice");
        person.greet();
    }
}
```

### Gestion des exceptions

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException ex) {
    System.out.println("Erreur : " + ex.getMessage());
} finally {
    System.out.println("Opération terminée.");
}
```

### Asynchronisme avec `CompletableFuture`

```java
import java.util.concurrent.CompletableFuture;

public class AsyncExample {
    public static void main(String[] args) {
        CompletableFuture.supplyAsync(() -> "Données récupérées")
            .thenAccept(System.out::println);
    }
}
```

### Utilisation des threads

```java
public class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Thread exécuté : " + Thread.currentThread().getName());
    }

    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start();
    }
}
```

---

## Développement d'API REST avec Java

### Exemple de contrôleur avec Spring Boot

```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {
    @GetMapping("/api/hello")
    public String sayHello() {
        return "Hello, API!";
    }
}
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

## Tests avec Java

### Utilisation de JUnit

Ajoutez JUnit au projet Maven :

```xml
<!-- filepath: pom.xml -->
<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter</artifactId>
    <version>5.9.0</version>
    <scope>test</scope>
</dependency>
```

Exemple de test :

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class CalculatorTest {
    @Test
    public void testAddition() {
        int result = 2 + 3;
        assertEquals(5, result);
    }
}
```

---

## Gestion des logs

Ajoutez les logs dans `application.properties` :

```properties
logging.level.org.springframework=DEBUG
logging.file.name=logs/application.log
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

## Bonnes pratiques

1. **Utiliser les conventions de nommage** : Respectez les conventions Java pour les classes, méthodes, et variables.
2. **Favoriser l'injection de dépendances** : Utilisez Spring ou un autre framework pour gérer les dépendances.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
4. **Structurer les projets** : Organisez les projets en couches (ex. contrôleurs, services, modèles, DTOs, entités) pour améliorer la maintenabilité.
5. **Utiliser Lombok** : Simplifiez le code en générant automatiquement les getters, setters, et autres méthodes courantes.
6. **Activer les logs** : Configurez des logs pour surveiller les performances et les erreurs.
7. **Sécuriser les endpoints** : Implémentez Spring Security pour protéger les endpoints sensibles.

---

## Liens utiles

- [Documentation officielle Java](https://docs.oracle.com/en/java/)
- [Documentation Spring Boot](https://spring.io/projects/spring-boot)
- [Tutoriels Java](https://www.w3schools.com/java/)
- [Exemples de projets Java](https://github.com/spring-projects/spring-boot/tree/main/spring-boot-samples)
- [Documentation Spring Data JPA](https://spring.io/projects/spring-data-jpa)
