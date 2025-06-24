# 📦 Java

## Introduction

Java est un langage de programmation orienté objet, robuste et multiplateforme. Il est utilisé pour développer des applications web, mobiles, de bureau, et des systèmes embarqués.

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

---

## Exemples pratiques

### Exemple de programme simple

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
```

### Utilisation des classes et objets

```java
class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    public void greet() {
        System.out.println("Hello, " + name + "!");
    }
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person("Alice");
        person.greet();
    }
}
```

### Gestion des exceptions

```java
public class Main {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Erreur : " + e.getMessage());
        }
    }
}
```

### Utilisation des threads

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread en cours d'exécution");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start();
    }
}
```

---

## Bonnes pratiques

1. **Utiliser les conventions de nommage** : Respectez les conventions Java pour les noms de classes, méthodes, et variables.
2. **Gérer les exceptions** : Implémentez une gestion robuste des exceptions pour éviter les plantages.
3. **Utiliser les collections** : Privilégiez les collections comme `ArrayList` et `HashMap` pour gérer les données dynamiques.

---

## Liens utiles

- [Documentation officielle Java](https://docs.oracle.com/en/java/)
- [Tutoriels Java](https://www.w3schools.com/java/)
- [Exemples de code Java](https://github.com/TheAlgorithms/Java)
