# 📦 Bootstrap

## Introduction

Bootstrap est un framework CSS populaire qui permet de créer des designs réactifs et modernes rapidement. Il offre une collection de composants préconçus et des classes utilitaires pour styliser les éléments HTML.

---

## Commandes essentielles

### Installation

```bash
npm install bootstrap
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

## Exemples pratiques

### Boutons

```html
<button class="btn btn-primary">Primary Button</button>
<button class="btn btn-secondary">Secondary Button</button>
```

### Grille responsive

```html
<div class="container">
  <div class="row">
    <div class="col-md-6">Colonne 1</div>
    <div class="col-md-6">Colonne 2</div>
  </div>
</div>
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

---

## Liens utiles

- [Documentation officielle Bootstrap](https://getbootstrap.com/docs)
- [Exemples Bootstrap](https://getbootstrap.com/docs/5.3/examples/)
- [CDN Bootstrap](https://www.bootstrapcdn.com/)
