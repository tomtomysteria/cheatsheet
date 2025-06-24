# 📦 HTML

## Introduction

HTML (HyperText Markup Language) est le langage standard utilisé pour structurer le contenu des pages web. Il permet de définir des éléments comme les titres, paragraphes, images, liens, et bien plus encore.

---

## Commandes essentielles

### Structure de base d'une page HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Title</title>
</head>
<body>
  <h1>Hello, HTML!</h1>
  <p>Bienvenue dans le monde du développement web.</p>
</body>
</html>
```

### Éléments HTML courants

```html
<!-- Liens -->
<a href="https://example.com">Visitez notre site</a>

<!-- Images -->
<img src="image.jpg" alt="Description de l'image">

<!-- Listes -->
<ul>
  <li>Élément 1</li>
  <li>Élément 2</li>
</ul>

<!-- Formulaires -->
<form action="/submit" method="POST">
  <label for="name">Nom :</label>
  <input type="text" id="name" name="name">
  <button type="submit">Envoyer</button>
</form>
```

---

## Exemples pratiques

### Intégration de CSS

Ajoutez des styles directement dans le fichier HTML.

```html
<style>
  body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    color: #333;
  }
</style>
```

### Intégration de JavaScript

Ajoutez des scripts pour rendre la page interactive.

```html
<script>
  document.addEventListener('DOMContentLoaded', () => {
    alert('Bienvenue sur la page HTML!');
  });
</script>
```

### Utilisation des tableaux

```html
<table border="1">
  <tr>
    <th>Nom</th>
    <th>Âge</th>
  </tr>
  <tr>
    <td>Alice</td>
    <td>30</td>
  </tr>
  <tr>
    <td>Bob</td>
    <td>25</td>
  </tr>
</table>
```

---

## Bonnes pratiques

1. **Utiliser des balises sémantiques** : Privilégiez les balises comme `<header>`, `<footer>`, `<article>`, et `<section>` pour améliorer l'accessibilité et le SEO.
2. **Valider le code HTML** : Utilisez des outils comme le [W3C Validator](https://validator.w3.org/) pour vérifier la validité du code.
3. **Optimiser les performances** : Minifiez le code HTML et utilisez des attributs comme `async` ou `defer` pour les scripts.

---

## Liens utiles

- [Documentation officielle HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [Tutoriels HTML](https://www.w3schools.com/html/)
- [Guide des balises HTML](https://htmlreference.io/)
