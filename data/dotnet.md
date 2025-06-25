# 📦 .NET / C \#

## Introduction

.NET est un framework de développement open-source créé par Microsoft. Il permet de construire des applications web, mobiles, de bureau, et cloud. Grâce à sa compatibilité avec C#, .NET offre une grande flexibilité, une riche bibliothèque de fonctionnalités, et une intégration facile avec des outils modernes comme Azure. C# est le langage principal utilisé avec .NET, offrant une syntaxe claire et puissante pour développer des applications robustes et scalables.

---

## Commandes essentielles

### .NET CLI

```bash
dotnet new console -n MyApp          # Crée un nouveau projet console
dotnet new webapi -n MyApi           # Crée un projet API REST
dotnet new mvc -n MyMvcApp           # Crée un projet MVC
dotnet new classlib -n MyLibrary     # Crée une bibliothèque de classes
dotnet run                           # Exécute le projet
dotnet build                         # Compile le projet
dotnet test                          # Exécute les tests
dotnet add package <package-name>    # Ajoute un package NuGet au projet
dotnet remove package <package-name> # Supprime un package NuGet du projet
dotnet restore                       # Restaure les dépendances du projet
dotnet publish -c Release            # Publie le projet pour la production
dotnet clean                         # Nettoie les fichiers générés par la compilation
dotnet list package                  # Liste les packages NuGet installés
dotnet watch run                     # Exécute le projet en mode veille
dotnet ef migrations add <name>      # Ajoute une migration Entity Framework
dotnet ef database update            # Applique les migrations à la base de données
```

---

## Concepts clés

### Classes et objets

```csharp
// filepath: Models/Person.cs
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
} finally {
    Console.WriteLine("Opération terminée.");
}
```

### Asynchronisme avec `async` et `await`

```csharp
public async Task<string> FetchDataAsync() {
    await Task.Delay(1000); // Simule une opération asynchrone
    return "Données récupérées";
}

class Program {
    static async Task Main() {
        string data = await new Program().FetchDataAsync();
        Console.WriteLine(data);
    }
}
```

---

## Développement d'API REST avec .NET

### Exemple de contrôleur REST

```csharp
// filepath: Controllers/HelloController.cs
using Microsoft.AspNetCore.Mvc;

[ApiController]
[Route("api/[controller]")]
public class HelloController : ControllerBase {
    [HttpGet]
    public IActionResult Get() {
        return Ok("Hello, .NET API!");
    }
}
```

### Exemple de modèle (DTO)

```csharp
// filepath: Models/UserDTO.cs
public class UserDTO {
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }
}
```

### Exemple d'entité avec Entity Framework

```csharp
// filepath: Entities/User.cs
using System.ComponentModel.DataAnnotations;

public class User {
    [Key]
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }
}
```

### Exemple de repository avec Entity Framework

```csharp
// filepath: Repositories/UserRepository.cs
using Microsoft.EntityFrameworkCore;

public class UserRepository {
    private readonly DbContext _context;

    public UserRepository(DbContext context) {
        _context = context;
    }

    public async Task<List<User>> GetAllUsersAsync() {
        return await _context.Set<User>().ToListAsync();
    }
}
```

### Exemple de service

```csharp
// filepath: Services/UserService.cs
public interface IUserService {
    Task<UserDTO> GetUserByIdAsync(int id);
}

public class UserService : IUserService {
    private readonly UserRepository _userRepository;

    public UserService(UserRepository userRepository) {
        _userRepository = userRepository;
    }

    public async Task<UserDTO> GetUserByIdAsync(int id) {
        var user = await _userRepository.GetAllUsersAsync();
        return user != null ? new UserDTO { Id = user.Id, Name = user.Name, Email = user.Email } : null;
    }
}
```

### Injection de dépendances

Ajoutez le service dans `Program.cs` :

```csharp
// filepath: Program.cs
var builder = WebApplication.CreateBuilder(args);
// ...existing code...
builder.Services.AddScoped<IUserService, UserService>();
builder.Services.AddScoped<UserRepository>();
builder.Services.AddDbContext<DbContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));
// ...existing code...
var app = builder.Build();
// ...existing code...
```

---

## Développement MVC avec .NET

### Exemple de contrôleur MVC

```csharp
// filepath: Controllers/HomeController.cs
using Microsoft.AspNetCore.Mvc;

public class HomeController : Controller {
    public IActionResult Index() {
        return View();
    }
}
```

### Exemple de vue Razor

Ajoutez une vue `Index.cshtml` dans le dossier `Views/Home` :

```html
<!-- filepath: Views/Home/Index.cshtml -->
@{
    ViewData["Title"] = "Accueil";
}

<h1>@ViewData["Title"]</h1>
<p>Bienvenue dans l'application MVC .NET !</p>
```

---

## Tests avec .NET

### Utilisation de xUnit

Ajoutez xUnit au projet :

```bash
dotnet add package xunit
```

Exemple de test :

```csharp
// filepath: Tests/CalculatorTests.cs
using Xunit;

public class CalculatorTests {
    [Fact]
    public void TestAddition() {
        int result = 2 + 3;
        Assert.Equal(5, result);
    }
}
```

---

## Gestion des logs

Ajoutez les logs dans `appsettings.json` :

```json
// filepath: appsettings.json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  }
}
```

Exemple d'utilisation des logs dans un service :

```csharp
// filepath: Services/LoggingService.cs
using Microsoft.Extensions.Logging;

public class LoggingService {
    private readonly ILogger<LoggingService> _logger;

    public LoggingService(ILogger<LoggingService> logger) {
        _logger = logger;
    }

    public void LogMessage(string message) {
        _logger.LogInformation("Message reçu : {Message}", message);
    }
}
```

---

## Bonnes pratiques

1. **Structurer les projets** : Organisez les projets en couches (ex. contrôleurs, services, modèles, DTOs, entités) pour améliorer la maintenabilité.
2. **Utiliser Entity Framework** : Simplifiez la gestion des bases de données avec Entity Framework.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
4. **Activer les logs** : Configurez des logs pour surveiller les performances et les erreurs.
5. **Sécuriser les endpoints** : Utilisez ASP.NET Core Identity ou JWT pour protéger les endpoints sensibles.
6. **Configurer les environnements** : Utilisez des fichiers `appsettings.json` ou des variables d'environnement pour gérer les configurations.

---

## Liens utiles

- [Documentation officielle .NET](https://learn.microsoft.com/en-us/dotnet/)
- [Tutoriels .NET](https://learn.microsoft.com/en-us/dotnet/core/tutorials/)
- [Exemples de projets .NET](https://github.com/dotnet/samples)
- [Documentation ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/)
- [Documentation Entity Framework](https://learn.microsoft.com/en-us/ef/)
