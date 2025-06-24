# 📦 Go

## Introduction

Go (ou Golang) est un langage de programmation conçu par Google. Il est connu pour sa simplicité, ses performances élevées, et son support natif pour la concurrence grâce aux goroutines.

---

## Commandes essentielles

### Gestion des fichiers

```bash
go run main.go               # Exécute un fichier Go
go build main.go             # Compile un fichier Go en binaire
go test ./...                # Exécute les tests dans le projet
go fmt ./...                 # Formate le code Go
go mod init <module-name>    # Initialise un module Go
go get <package>             # Installe un package externe
```

### Gestion des modules

```bash
go mod tidy                  # Nettoie les dépendances inutilisées
go list -m all               # Liste les modules utilisés
```

---

## Exemples pratiques

### Exemple de programme simple

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, Go!")
}
```

### Utilisation des goroutines

Les goroutines permettent d'exécuter des fonctions de manière concurrente.

```go
package main

import (
    "fmt"
    "time"
)

func sayHello() {
    fmt.Println("Hello!")
}

func main() {
    go sayHello()
    time.Sleep(1 * time.Second) // Attendre pour voir le résultat
}
```

### Gestion des erreurs

```go
package main

import (
    "errors"
    "fmt"
)

func divide(a, b float64) (float64, error) {
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

---

## Bonnes pratiques

1. **Utiliser `go fmt`** : Formatez le code pour garantir une lisibilité uniforme.
2. **Gérer les erreurs explicitement** : Vérifiez et gérez les erreurs pour éviter les comportements imprévus.
3. **Utiliser les tests unitaires** : Implémentez des tests avec `go test` pour garantir la qualité du code.

---

## Liens utiles

- [Documentation officielle Go](https://golang.org/doc/)
- [Tutoriels Go](https://tour.golang.org/)
- [Exemples de code Go](https://github.com/golang/go/wiki/CodeExamples)
