# 📦 SCSS

## Introduction

SCSS (Sassy CSS) est une extension de CSS qui ajoute des fonctionnalités avancées comme les variables, les mixins, les fonctions, et les imbrications. Il simplifie la gestion des styles complexes et améliore la maintenabilité des projets.

---

## Commandes essentielles

### Installation et compilation

```bash
npm install sass                      # Installe Sass via npm
sass input.scss output.css            # Compile un fichier SCSS en CSS
sass --watch input.scss output.css    # Active la compilation automatique
```

### Options avancées

```bash
sass --style compressed input.scss output.css  # Minifie le fichier CSS généré
sass --source-map input.scss output.css        # Génère une carte source pour le débogage
```

---

## Exemples pratiques

### Utilisation des variables

```scss
$primary-color: #3498db;
$secondary-color: #2ecc71;

body {
  background-color: $primary-color;
  color: $secondary-color;
}
```

### Imbrication des sélecteurs

```scss
nav {
  ul {
    list-style: none;
    li {
      display: inline-block;
      a {
        text-decoration: none;
        color: #333;
      }
    }
  }
}
```

### Utilisation des mixins

```scss
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  @include flex-center;
  height: 100vh;
}
```

### Héritage avec `@extend`

```scss
.button {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
}

.primary-button {
  @extend .button;
  background-color: #3498db;
  color: white;
}
```

### Fonctions personnalisées

```scss
@function calculate-rem($size) {
  @return $size / 16 * 1rem;
}

h1 {
  font-size: calculate-rem(32px);
}
```

---

## Bonnes pratiques

1. **Organiser les fichiers SCSS** : Divisez les styles en fichiers comme `variables.scss`, `mixins.scss`, et `base.scss` pour une meilleure maintenabilité.
2. **Utiliser des conventions de nommage** : Adoptez des conventions claires pour les noms de variables et mixins.
3. **Minimiser le CSS généré** : Utilisez l'option `--style compressed` pour réduire la taille des fichiers CSS en production.

---

## Liens utiles

- [Documentation officielle SCSS](https://sass-lang.com/documentation)
- [Tutoriels SCSS](https://www.w3schools.com/sass/)
- [Exemples de projets SCSS](https://github.com/sass/sass/tree/main/examples)
