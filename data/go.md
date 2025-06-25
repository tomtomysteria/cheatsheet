# 📦 Go

## Introduction

Go (ou Golang) est un langage de programmation open-source développé par Google. Il est conçu pour être simple, performant, et concurrentiel. Go est idéal pour développer des API REST, des microservices, et des applications cloud grâce à ses fonctionnalités intégrées comme les goroutines et les canaux. Il est particulièrement adapté aux systèmes distribués et aux applications nécessitant une haute performance.

---

## Commandes essentielles

### Go CLI

```bash
go mod init <module-name>            # Initialise un nouveau module Go
go build                             # Compile le projet
go run <file>.go                     # Exécute un fichier Go
go test                              # Exécute les tests
go fmt                               # Formate le code Go
go get <package>                     # Installe un package
go mod tidy                          # Nettoie les dépendances inutilisées
go list                              # Liste les modules et dépendances
go env                               # Affiche les variables d'environnement Go
```

---

## Concepts clés

### Exemple de fonction

```go
package main

import "fmt"

func add(a int, b int) int {
    return a + b
}

func main() {
    fmt.Println(add(5, 3)) // 8
}
```

### Gestion des erreurs

```go
package main

import (
    "errors"
    "fmt"
)

func divide(a, b int) (int, error) {
    if b == 0 {
        return 0, errors.New("division par zéro")
    }
    return a / b, nil
}

func main() {
    result, err := divide(10, 0)
    if err != nil {
        fmt.Println("Erreur :", err)
    } else {
        fmt.Println("Résultat :", result)
    }
}
```

### Utilisation des goroutines

```go
package main

import (
    "fmt"
    "time"
)

func printMessage(message string) {
    for i := 0; i < 5; i++ {
        fmt.Println(message)
        time.Sleep(500 * time.Millisecond)
    }
}

func main() {
    go printMessage("Goroutine 1")
    go printMessage("Goroutine 2")

    time.Sleep(3 * time.Second)
    fmt.Println("Fin du programme")
}
```

---

## Développement d'API REST avec Go

### Exemple de contrôleur avec Gin

```go
package main

import (
    "github.com/gin-gonic/gin"
)

func main() {
    r := gin.Default()

    r.GET("/api/hello", func(c *gin.Context) {
        c.JSON(200, gin.H{
            "message": "Hello, Go API!",
        })
    })

    r.Run(":8080") // Démarre le serveur sur le port 8080
}
```

### Exemple de modèle (DTO)

```go
package models

type UserDTO struct {
    ID    int    `json:"id"`
    Name  string `json:"name"`
    Email string `json:"email"`
}
```

### Exemple d'entité avec GORM

```go
package entities

import "gorm.io/gorm"

type User struct {
    gorm.Model
    Name  string `json:"name"`
    Email string `json:"email"`
}
```

### Exemple de repository avec GORM

```go
package repositories

import (
    "gorm.io/gorm"
    "example/entities"
)

type UserRepository struct {
    db *gorm.DB
}

func NewUserRepository(db *gorm.DB) *UserRepository {
    return &UserRepository{db: db}
}

func (r *UserRepository) FindAll() ([]entities.User, error) {
    var users []entities.User
    err := r.db.Find(&users).Error
    return users, err
}
```

### Exemple de service

```go
package services

import (
    "example/repositories"
    "example/models"
)

type UserService struct {
    userRepository *repositories.UserRepository
}

func NewUserService(userRepository *repositories.UserRepository) *UserService {
    return &UserService{userRepository: userRepository}
}

func (s *UserService) GetUserByID(id int) models.UserDTO {
    user, _ := s.userRepository.FindAll()
    return models.UserDTO{
        ID:    user[0].ID,
        Name:  user[0].Name,
        Email: user[0].Email,
    }
}
```

---

## Tests avec Go

### Utilisation de `testing`

Exemple de test :

```go
package main

import (
    "testing"
)

func TestAdd(t *testing.T) {
    result := add(2, 3)
    if result != 5 {
        t.Errorf("add(2, 3) = %d; want 5", result)
    }
}
```

Exécutez les tests :

```bash
go test
```

---

## Gestion des logs

### Utilisation de `log`

```go
package main

import (
    "log"
)

func main() {
    log.Println("Info : opération réussie")
    log.Println("Avertissement : attention à cette étape")
    log.Println("Erreur : une exception est survenue")
}
```

---

## Bonnes pratiques

1. **Structurer les projets** : Organisez les projets en packages pour améliorer la maintenabilité.
2. **Utiliser les interfaces** : Simplifiez les tests et les extensions avec des interfaces.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
4. **Activer les logs** : Configurez des logs pour surveiller les performances et les erreurs.
5. **Utiliser les goroutines** : Implémentez des opérations concurrentes avec les goroutines.
6. **Utiliser GORM** : Simplifiez la gestion des bases de données avec GORM.
7. **Minimiser les dépendances** : Utilisez uniquement les packages nécessaires pour réduire la complexité.

---

## Liens utiles

- [Documentation officielle Go](https://golang.org/doc/)
- [Tutoriels Go](https://golang.org/doc/tutorial/)
- [Exemples de projets Go](https://github.com/golang/example)
- [Documentation Gin](https://gin-gonic.com/docs/)
- [Documentation GORM](https://gorm.io/docs/)
