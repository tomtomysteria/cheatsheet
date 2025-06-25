# 📦 HTML

## Introduction

HTML (HyperText Markup Language) est le langage standard utilisé pour structurer le contenu des pages web. Il permet de définir des éléments comme les titres, paragraphes, images, liens, et formulaires. HTML est la base de tout développement web et fonctionne en synergie avec CSS et JavaScript pour créer des interfaces utilisateur interactives.

---

## Concepts clés

### Structure de base d'une page HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Bienvenue dans HTML</h1>
    <p>Ceci est une page HTML de base.</p>
</body>
</html>
```

---

### Balises HTML essentielles

#### Titres (`<h1>` à `<h6>`)

Les balises de titre permettent de structurer le contenu en niveaux hiérarchiques. `<h1>` est le titre principal, tandis que `<h6>` est le niveau le plus bas.

```html
<h1>Titre principal</h1>
<h2>Sous-titre niveau 2</h2>
<h3>Sous-titre niveau 3</h3>
<h4>Sous-titre niveau 4</h4>
<h5>Sous-titre niveau 5</h5>
<h6>Sous-titre niveau 6</h6>
```

#### Paragraphes

```html
<p>Ceci est un paragraphe.</p>
```

#### Liens et images

```html
<a href="https://example.com">Visitez notre site</a>
<img src="image.jpg" alt="Description de l'image">
```

#### Listes

```html
<ul>
    <li>Élément de liste non ordonnée</li>
    <li>Autre élément</li>
</ul>

<ol>
    <li>Élément de liste ordonnée</li>
    <li>Autre élément</li>
</ol>
```

#### Tableaux

```html
<table>
    <thead>
        <tr>
            <th>Nom</th>
            <th>Âge</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Jean</td>
            <td>30</td>
        </tr>
        <tr>
            <td>Marie</td>
            <td>25</td>
        </tr>
    </tbody>
</table>
```

---

### HTML5 : Nouveautés et concepts clés

HTML5 est la dernière version majeure de HTML. Elle introduit des balises sémantiques, des fonctionnalités multimédia, et des API JavaScript avancées pour les applications web modernes.

#### Balises sémantiques

HTML5 propose des balises comme `<header>`, `<main>`, `<footer>`, `<article>`, et `<aside>` pour structurer le contenu de manière plus claire et améliorer l'accessibilité.

```html
<header>
    <h1>Titre principal</h1>
</header>
<main>
    <article>
        <h2>Article</h2>
        <p>Contenu de l'article.</p>
    </article>
    <aside>
        <p>Informations complémentaires.</p>
    </aside>
</main>
<footer>
    <p>© 2023 Mon Site</p>
</footer>
```

#### Multimédia

HTML5 simplifie l'intégration de vidéos et audios sans plugins externes.

```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    Votre navigateur ne supporte pas la balise vidéo.
</video>

<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    Votre navigateur ne supporte pas la balise audio.
</audio>
```

#### API JavaScript

HTML5 introduit des API comme Canvas pour le dessin 2D, Local Storage pour le stockage persistant, et Geolocation pour accéder à la position géographique de l'utilisateur.

```html
<canvas id="myCanvas" width="200" height="100"></canvas>
<script>
    const canvas = document.getElementById('myCanvas');
    const ctx = canvas.getContext('2d');
    ctx.fillStyle = 'blue';
    ctx.fillRect(10, 10, 150, 75);
</script>
```

---

### Styles dans HTML

#### Balise `<style>`

La balise `<style>` permet d'ajouter des styles CSS directement dans le fichier HTML.

```html
<style>
    body {
        font-family: Arial, sans-serif;
        background-color: #f0f0f0;
    }

    h1 {
        color: #3498db;
    }
</style>
```

#### Style inline

Le style inline permet d'ajouter des styles directement dans les balises HTML via l'attribut `style`.

```html
<p style="color: red; font-size: 18px;">Ce texte est stylisé en rouge avec une taille de 18px.</p>
```

---

### Balise `<script>`

La balise `<script>` permet d'ajouter du JavaScript directement dans le fichier HTML.

```html
<script>
    document.addEventListener('DOMContentLoaded', () => {
        alert('Bienvenue sur la page HTML !');
    });
</script>
```

---

### Attributs HTML

#### Attributs courants

```html
<a href="https://example.com" target="_blank" rel="noopener">Lien externe</a>
<img src="image.jpg" alt="Description de l'image" width="300" height="200">
<input type="text" placeholder="Entrez votre nom">
```

#### Attributs de données

```html
<div data-role="admin" data-id="123">Contenu</div>
```

---

### Formulaires HTML

#### Exemple de formulaire

```html
<form action="/submit" method="POST">
    <label for="name">Nom :</label>
    <input type="text" id="name" name="name" required>

    <label for="email">Email :</label>
    <input type="email" id="email" name="email" required>

    <button type="submit">Envoyer</button>
</form>
```

#### Types d'input

```html
<input type="text" placeholder="Texte">
<input type="password" placeholder="Mot de passe">
<input type="email" placeholder="Email">
<input type="number" placeholder="Nombre">
<input type="checkbox"> Cochez-moi
<input type="radio" name="option" value="1"> Option 1
<input type="radio" name="option" value="2"> Option 2
```

---

## Enjeux du développement HTML

1. **Accessibilité** : Les pages HTML doivent être accessibles à tous, y compris aux personnes ayant des handicaps. Utilisez des balises sémantiques et des attributs comme `alt` pour les images.
2. **SEO (Search Engine Optimization)** : Structurez le contenu avec des balises sémantiques pour améliorer le référencement naturel.
3. **Compatibilité** : Assurez-vous que les pages fonctionnent correctement sur différents navigateurs et appareils.
4. **Performance** : Optimisez les fichiers HTML pour réduire le temps de chargement des pages.
5. **Sécurité** : Validez les données des formulaires côté client et côté serveur pour éviter les attaques XSS.

---

## Bonnes pratiques

1. **Structurer le contenu** : Utilisez des balises sémantiques comme `<header>`, `<main>`, `<footer>` pour améliorer l'accessibilité.
2. **Ajouter des descriptions** : Utilisez l'attribut `alt` pour les images afin de les rendre accessibles.
3. **Valider les formulaires** : Ajoutez des attributs comme `required` et `pattern` pour valider les données côté client.
4. **Optimiser les performances** : Minifiez les fichiers HTML et utilisez des outils comme gzip pour réduire leur taille.
5. **Utiliser des attributs de données** : Simplifiez la gestion des données dynamiques avec `data-*`.
6. **Tester la compatibilité** : Vérifiez le rendu des pages sur différents navigateurs et appareils.
7. **Respecter les standards** : Validez le code HTML avec des outils comme le W3C Validator.

---

## Liens utiles

- [Documentation officielle HTML5](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
- [Tutoriels HTML5](https://www.w3schools.com/html/html5_intro.asp)
- [Exemples de projets HTML5](https://github.com/html5rocks)
- [Validator W3C](https://validator.w3.org/)
