# 📦 .NET

## Introduction

.NET est un framework multiplateforme développé par Microsoft. Il permet de créer des applications web, mobiles, de bureau, et cloud. Il prend en charge plusieurs langages, notamment C#, F#, et Visual Basic.

---

## Commandes essentielles

### Gestion des projets

```bash
dotnet new console -n MyApp    # Crée un nouveau projet console
dotnet new webapi -n MyApi     # Crée un projet API web
dotnet new mvc -n MyMvcApp     # Crée un projet MVC
dotnet run                     # Exécute le projet
dotnet build                   # Compile le projet
dotnet publish -o ./publish    # Publie le projet
```

### Gestion des packages

```bash
dotnet add package <package-name>    # Ajoute un package NuGet
dotnet remove package <package-name> # Supprime un package NuGet
dotnet list package                  # Liste les packages installés
```

### Tests

```bash
dotnet test                          # Exécute les tests
dotnet new xunit -n MyTests          # Crée un projet de tests avec xUnit
```

---

## Exemples pratiques

### Exemple de programme console

```csharp
using System;

class Program {
    static void Main() {
        Console.WriteLine("Hello, .NET!");
    }
}
```

### Exemple d'API Web

```csharp
using Microsoft.AspNetCore.Mvc;

[ApiController]
[Route("[controller]")]
public class HelloController : ControllerBase {
    [HttpGet]
    public string Get() {
        return "Hello, .NET API!";
    }
}
```

### Utilisation des dépendances NuGet

Ajoutez un package comme `Newtonsoft.Json` pour gérer le JSON :

```bash
dotnet add package Newtonsoft.Json
```

Exemple d'utilisation :

```csharp
using Newtonsoft.Json;

class Program {
    static void Main() {
        var obj = new { Name = "Alice", Age = 30 };
        string json = JsonConvert.SerializeObject(obj);
        Console.WriteLine(json);
    }
}
```

---

## Bonnes pratiques

1. **Utiliser les outils de diagnostic** : Utilisez `dotnet trace` et `dotnet dump` pour diagnostiquer les performances et les erreurs.
2. **Versionner les fichiers de configuration** : Ajoutez `appsettings.json` et `launchSettings.json` au contrôle de version.
3. **Utiliser les tests automatisés** : Implémentez des tests unitaires et d'intégration pour garantir la qualité du code.

---

## Liens utiles

- [Documentation officielle .NET](https://learn.microsoft.com/en-us/dotnet/)
- [Tutoriels .NET](https://learn.microsoft.com/en-us/dotnet/tutorials/)
- [NuGet Gallery](https://www.nuget.org/)
