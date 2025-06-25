# 📦 Kotlin

## Introduction

Kotlin est un langage de programmation moderne, concis et sécurisé, développé par JetBrains. Il est entièrement compatible avec Java et est utilisé pour développer des applications Android, des services backend, et des applications multiplateformes. Kotlin est conçu pour améliorer la productivité des développeurs tout en réduisant les erreurs.

---

## Commandes essentielles

### Gradle CLI

```bash
gradle init --type kotlin-application # Initialise un projet Kotlin
gradle build                          # Compile et construit le projet
gradle run                            # Exécute l'application
gradle test                           # Exécute les tests
gradle clean                          # Nettoie les fichiers générés
gradle dependencies                   # Liste les dépendances du projet
gradle assemble                       # Prépare les fichiers pour la distribution
```

### Kotlin CLI

```bash
kotlinc main.kt -include-runtime -d main.jar # Compile un fichier Kotlin en JAR
kotlin main.jar                              # Exécute un fichier JAR Kotlin
kotlinc -script script.kts                   # Exécute un script Kotlin
```

---

## Concepts clés

### Classes et objets

```kotlin
class Person(val name: String) {
    fun greet() {
        println("Hello, $name!")
    }
}

fun main() {
    val person = Person("Alice")
    person.greet()
}
```

### Fonctions

```kotlin
fun add(a: Int, b: Int): Int {
    return a + b
}

fun main() {
    println(add(5, 3)) // 8
}
```

### Gestion des erreurs

```kotlin
fun parseJson(json: String): Map<String, String> {
    return try {
        mapOf("key" to json) // Simule un parsing JSON
    } catch (e: Exception) {
        println("Erreur : ${e.message}")
        emptyMap()
    }
}

fun main() {
    val result = parseJson("{\"key\": \"value\"}")
    println(result)
}
```

---

## Développement backend avec Kotlin

### Exemple de contrôleur avec Spring Boot

```kotlin
import org.springframework.web.bind.annotation.GetMapping
import org.springframework.web.bind.annotation.RestController

@RestController
class HelloController {
    @GetMapping("/api/hello")
    fun sayHello(): String {
        return "Hello, Kotlin Backend!"
    }
}
```

### Exemple de modèle (DTO)

```kotlin
data class UserDTO(
    val id: Long,
    val name: String,
    val email: String
)
```

### Exemple d'entité avec JPA

```kotlin
import jakarta.persistence.Entity
import jakarta.persistence.Id

@Entity
data class User(
    @Id val id: Long,
    val name: String,
    val email: String
)
```

### Exemple de repository avec Spring Data JPA

```kotlin
import org.springframework.data.jpa.repository.JpaRepository

interface UserRepository : JpaRepository<User, Long>
```

### Exemple de service

```kotlin
import org.springframework.stereotype.Service

@Service
class UserService(private val userRepository: UserRepository) {
    fun getUserById(id: Long): User? {
        return userRepository.findById(id).orElse(null)
    }
}
```

---

## Développement Android avec Kotlin

### Exemple d'activité Android

```kotlin
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        println("Hello, Android!")
    }
}
```

### Exemple de ViewModel avec Jetpack

```kotlin
import androidx.lifecycle.ViewModel

class MainViewModel : ViewModel() {
    val message = "Hello, ViewModel!"
}
```

---

## Tests avec Kotlin

### Utilisation de JUnit

Ajoutez JUnit au projet Gradle :

```groovy
dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter:5.9.0'
}
```

Exemple de test :

```kotlin
import org.junit.jupiter.api.Assertions.assertEquals
import org.junit.jupiter.api.Test

class CalculatorTest {
    @Test
    fun testAddition() {
        val result = 2 + 3
        assertEquals(5, result)
    }
}
```

---

## Gestion des logs

### Utilisation de `Log` pour Android

```kotlin
import android.util.Log

fun logMessage(message: String) {
    Log.d("MainActivity", message)
}
```

### Utilisation de SLF4J pour les applications backend

Ajoutez SLF4J au projet Gradle :

```groovy
dependencies {
    implementation 'org.slf4j:slf4j-api:1.7.36'
    implementation 'org.slf4j:slf4j-simple:1.7.36'
}
```

Exemple de configuration :

```kotlin
import org.slf4j.LoggerFactory

class LoggingService {
    private val logger = LoggerFactory.getLogger(LoggingService::class.java)

    fun logInfo(message: String) {
        logger.info("Info : $message")
    }

    fun logError(error: String) {
        logger.error("Erreur : $error")
    }
}
```

---

## Bonnes pratiques

1. **Utiliser les extensions Kotlin** : Simplifiez le code avec les fonctions d'extension.
2. **Favoriser les immutabilités** : Utilisez `val` pour les variables constantes.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
4. **Activer les logs** : Configurez des logs pour surveiller les performances et les erreurs.
5. **Utiliser les coroutines** : Implémentez des opérations asynchrones avec `suspend` et `CoroutineScope`.
6. **Structurer les projets** : Organisez les projets en modules pour améliorer la maintenabilité.
7. **Utiliser les DTOs** : Validez et transférez les données avec des objets dédiés.
8. **Sécuriser les endpoints** : Implémentez Spring Security pour protéger les endpoints sensibles.

---

## Liens utiles

- [Documentation officielle Kotlin](https://kotlinlang.org/docs/home.html)
- [Tutoriels Kotlin](https://kotlinlang.org/docs/tutorials.html)
- [Documentation Android avec Kotlin](https://developer.android.com/kotlin)
- [Exemples de projets Kotlin](https://github.com/Kotlin/kotlin-examples)
- [Documentation Spring Boot](https://spring.io/projects/spring-boot)
