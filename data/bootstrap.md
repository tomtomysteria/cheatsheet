# 📦 Bootstrap

## Introduction

Bootstrap est un framework CSS populaire qui permet de créer des designs réactifs et modernes rapidement. Il offre une collection de composants préconçus et des classes utilitaires pour styliser les éléments HTML.

---

## Commandes essentielles

### Installation

```bash
npm install bootstrap                # Installe Bootstrap via npm
```

### Intégration dans un projet

Ajoutez Bootstrap à votre projet via un CDN ou en utilisant les fichiers téléchargés.

#### Via CDN

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
```

#### Via fichiers locaux

```html
<link href="path/to/bootstrap.min.css" rel="stylesheet">
<script src="path/to/bootstrap.bundle.min.js"></script>
```

---

## Concepts clés

### Grille responsive

La grille Bootstrap est basée sur un système de colonnes flexibles.

```html
<div class="container">
  <div class="row">
    <div class="col-md-6">Colonne 1</div>
    <div class="col-md-6">Colonne 2</div>
  </div>
</div>
```

### Classes utilitaires

Bootstrap propose des classes utilitaires pour styliser rapidement les éléments.

- **Espacement** : `m-3`, `p-4`
- **Couleurs** : `bg-primary`, `text-danger`
- **Alignement** : `text-center`, `float-end`
- **Visibilité** : `d-none`, `d-md-block`

---

## Composants Bootstrap

### Boutons

```html
<button class="btn btn-primary">Primary Button</button>
<button class="btn btn-secondary">Secondary Button</button>
```

### Formulaires

```html
<form>
  <div class="mb-3">
    <label for="email" class="form-label">Adresse email</label>
    <input type="email" class="form-control" id="email" placeholder="name@example.com">
  </div>
  <button type="submit" class="btn btn-success">Envoyer</button>
</form>
```

### Modals

```html
<!-- Bouton pour ouvrir le modal -->
<button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">
  Ouvrir le modal
</button>

<!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Titre du modal</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        Contenu du modal.
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Fermer</button>
        <button type="button" class="btn btn-primary">Sauvegarder</button>
      </div>
    </div>
  </div>
</div>
```

### Alertes

```html
<div class="alert alert-success" role="alert">
  Opération réussie !
</div>
<div class="alert alert-danger" role="alert">
  Une erreur est survenue.
</div>
```

### Navigation

```html
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <a class="navbar-brand" href="#">Navbar</a>
  <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarNav">
    <ul class="navbar-nav">
      <li class="nav-item">
        <a class="nav-link active" href="#">Accueil</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">À propos</a>
      </li>
    </ul>
  </div>
</nav>
```

---

## Bonnes pratiques

1. **Utiliser les classes utilitaires** : Exploitez les classes utilitaires pour éviter d'écrire du CSS personnalisé.
2. **Configurer les breakpoints** : Adaptez les designs aux différents écrans en utilisant les classes responsives.
3. **Minimiser les fichiers CSS** : Utilisez les versions minifiées pour améliorer les performances.
4. **Tester sur plusieurs navigateurs** : Assurez-vous que votre design fonctionne sur tous les navigateurs modernes.

---

## Liens utiles

- [Documentation officielle Bootstrap](https://getbootstrap.com/docs)
- [Exemples Bootstrap](https://getbootstrap.com/docs/5.3/examples/)
- [CDN Bootstrap](https://www.bootstrapcdn.com/)
