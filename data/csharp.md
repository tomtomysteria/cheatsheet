# 📦 C #

## Introduction

C# est un langage de programmation orienté objet développé par Microsoft. Il est utilisé pour créer des applications Windows, des jeux, des services web, et bien plus encore.

---

## Commandes essentielles

### .NET CLI

```bash
dotnet new console -n MyApp    # Crée un nouveau projet console
dotnet run                     # Exécute le projet
dotnet build                   # Compile le projet
dotnet test                    # Exécute les tests
```

---

## Exemples pratiques

### Exemple de programme simple

```csharp
using System;

class Program {
    static void Main() {
        Console.WriteLine("Hello, C#!");
    }
}
```

### Utilisation des classes et objets

```csharp
public class Person {
    public string Name { get; set; }

    public void Greet() {
        Console.WriteLine($"Hello, {Name}!");
    }
}

class Program {
    static void Main() {
        Person person = new Person { Name = "Alice" };
        person.Greet();
    }
}
```

### Gestion des exceptions

```csharp
try {
    int result = 10 / 0;
} catch (DivideByZeroException ex) {
    Console.WriteLine($"Erreur : {ex.Message}");
}
```

---

## Bonnes pratiques

1. **Utiliser les propriétés automatiques** : Simplifiez la gestion des attributs avec des propriétés automatiques.
2. **Utiliser `async` et `await`** : Implémentez des opérations asynchrones pour améliorer les performances.
3. **Respecter les conventions de nommage** : Utilisez des noms significatifs pour les classes, méthodes, et variables.

---

## Liens utiles

- [Documentation officielle C#](https://learn.microsoft.com/en-us/dotnet/csharp/)
- [Tutoriels C#](https://learn.microsoft.com/en-us/dotnet/csharp/tutorials/)
- [Exemples de code C#](https://github.com/dotnet/samples)
