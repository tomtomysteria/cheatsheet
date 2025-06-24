# 📦 Kotlin

## Introduction

Kotlin est un langage de programmation moderne, concis et sécurisé, conçu pour interagir avec Java. Il est largement utilisé pour le développement Android, les applications backend, et les projets multiplateformes.

---

## Commandes essentielles

### Compilation et exécution

```bash
kotlinc Main.kt -include-runtime -d Main.jar  # Compile un fichier Kotlin en JAR exécutable
java -jar Main.jar                            # Exécute le fichier JAR
```

### Gestion des dépendances avec Gradle

Ajoutez Kotlin à un projet Gradle :

```groovy
plugins {
    id 'org.jetbrains.kotlin.jvm' version '1.8.0'
}

dependencies {
    implementation "org.jetbrains.kotlin:kotlin-stdlib"
}
```

---

## Exemples pratiques

### Exemple de programme simple

```kotlin
fun main() {
    println("Hello, Kotlin!")
}
```

### Utilisation des classes et objets

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

### Gestion des exceptions

```kotlin
fun divide(a: Int, b: Int): Int {
    return try {
        a / b
    } catch (e: ArithmeticException) {
        println("Erreur : ${e.message}")
        0
    }
}

fun main() {
    println(divide(10, 0))
}
```

### Extensions de fonctions

```kotlin
fun String.capitalizeWords(): String {
    return split(" ").joinToString(" ") { it.capitalize() }
}

fun main() {
    val text = "hello kotlin world"
    println(text.capitalizeWords())
}
```

---

## Bonnes pratiques

1. **Utiliser les extensions** : Simplifiez le code en ajoutant des extensions aux classes existantes.
2. **Favoriser les immutabilités** : Utilisez `val` pour déclarer des variables immuables.
3. **Utiliser les coroutines** : Implémentez des opérations asynchrones avec `kotlinx.coroutines`.

---

## Liens utiles

- [Documentation officielle Kotlin](https://kotlinlang.org/docs/)
- [Tutoriels Kotlin](https://kotlinlang.org/docs/tutorials.html)
- [Exemples de code Kotlin](https://github.com/Kotlin/kotlin-examples)
