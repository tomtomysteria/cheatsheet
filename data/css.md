# 📦 CSS

## Introduction

CSS (Cascading Style Sheets) est utilisé pour styliser les pages web. Il permet de contrôler l'apparence des éléments HTML, comme les couleurs, les polices, les marges, et les dispositions.

---

## Commandes essentielles

### Syntaxe de base

```css
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  color: #333;
}

h1 {
  font-size: 2em;
  text-align: center;
}
```

### Sélecteurs CSS

```css
/* Sélecteur universel */
* {
  margin: 0;
  padding: 0;
}

/* Sélecteur de classe */
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}

/* Sélecteur d'identifiant */
#header {
  background-color: #3498db;
  color: white;
}

/* Sélecteur descendant */
nav ul li {
  list-style: none;
}
```

---

## Exemples pratiques

### Mise en page avec Flexbox

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.item {
  flex: 1;
  padding: 20px;
  background-color: #e74c3c;
  color: white;
}
```

### Mise en page avec Grid

```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}

.grid-item {
  background-color: #2ecc71;
  padding: 20px;
  text-align: center;
}
```

### Animation CSS

```css
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.fade-in {
  animation: fadeIn 2s ease-in-out;
}
```

---

## Bonnes pratiques

1. **Utiliser des classes réutilisables** : Créez des classes génériques pour éviter la duplication de styles.
2. **Organiser les fichiers CSS** : Divisez les styles en fichiers pour une meilleure maintenabilité (ex. `base.css`, `layout.css`, `components.css`).
3. **Utiliser des préprocesseurs CSS** : SCSS ou LESS peuvent simplifier la gestion des styles complexes.

---

## Liens utiles

- [Documentation officielle CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [Guide Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Guide Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
