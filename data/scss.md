# 📦 SCSS

## Introduction

SCSS (Sassy CSS) est une extension de CSS qui ajoute des fonctionnalités avancées comme les variables, les mixins, le nesting, l'héritage, et les fonctions personnalisées. Il simplifie la gestion des styles et améliore la maintenabilité des projets. SCSS est largement utilisé dans les projets modernes grâce à sa compatibilité avec CSS et ses outils puissants. Il permet de structurer les styles de manière modulaire et de réduire les répétitions.

---

## Commandes essentielles

### Installation de Sass

```bash
npm install -g sass                   # Installe Sass globalement
sass --version                        # Vérifie la version installée
```

### Sass CLI

```bash
sass <input.scss> <output.css>        # Compile un fichier SCSS en CSS
sass --watch <input.scss>:<output.css> # Surveille les changements et compile automatiquement
sass --style compressed               # Minifie le fichier CSS généré
sass --source-map                     # Génère une source map pour le fichier CSS
sass --update                         # Met à jour les fichiers SCSS compilés
```

---

## Concepts clés

### Variables SCSS

Les variables permettent de stocker des valeurs réutilisables.

```scss
$primary-color: #3498db;
$font-size: 16px;

body {
    color: $primary-color;
    font-size: $font-size;
}
```

---

### Mixins

Les mixins permettent de définir des blocs de styles réutilisables.

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

---

### Nesting

Le nesting permet d'imbriquer les styles pour refléter la structure HTML.

```scss
nav {
    ul {
        list-style: none;

        li {
            display: inline-block;

            a {
                text-decoration: none;
                color: #333;

                &:hover {
                    color: #3498db;
                }
            }
        }
    }
}
```

---

### Héritage

L'héritage permet de partager des styles entre sélecteurs.

```scss
%button-styles {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
}

.button-primary {
    @extend %button-styles;
    background-color: #3498db;
    color: white;
}

.button-secondary {
    @extend %button-styles;
    background-color: #95a5a6;
    color: black;
}

/* Extension d'une classe existante */
.button-large {
    @extend .button-primary;
    font-size: 18px;
}
```

---

### Fonctions personnalisées

Les fonctions personnalisées permettent de créer des calculs ou des transformations réutilisables.

```scss
@function calculate-rem($size) {
    $base-size: 16px;
    @return $size / $base-size * 1rem;
}

body {
    font-size: calculate-rem(24px);
}
```

---

## Responsive Design avec SCSS

### Utilisation des media queries

```scss
$mobile-breakpoint: 768px;

body {
    font-size: 16px;

    @media (max-width: $mobile-breakpoint) {
        font-size: 14px;
    }
}
```

---

## Enjeux du développement SCSS

1. **Performance** : Les fichiers SCSS doivent être compilés et optimisés pour réduire le temps de chargement des pages.
2. **Modularité** : Les styles doivent être organisés en modules pour faciliter la réutilisation et la maintenance.
3. **Scalabilité** : Les styles doivent être conçus pour évoluer avec le projet sans devenir difficiles à gérer.
4. **Compatibilité** : Les styles doivent fonctionner correctement sur différents navigateurs et appareils.
5. **Collaboration** : SCSS facilite la collaboration entre les développeurs grâce à sa structure claire et ses fonctionnalités avancées.

---

## Bonnes pratiques

1. **Structurer les styles** : Organisez les fichiers SCSS en modules pour améliorer la maintenabilité.
2. **Utiliser des variables** : Centralisez les couleurs, tailles, et autres valeurs dans un fichier `_variables.scss`.
3. **Réutiliser les mixins** : Simplifiez les styles répétitifs avec des mixins.
4. **Activer le responsive design** : Utilisez des media queries pour adapter les styles aux différents écrans.
5. **Minimiser l'héritage** : Utilisez l'héritage avec parcimonie pour éviter les conflits de styles.
6. **Automatiser les tâches** : Intégrez des outils comme Sass ou PostCSS pour compiler et optimiser les fichiers SCSS.
7. **Tester les styles** : Vérifiez la compatibilité des styles sur différents navigateurs et appareils.
8. **Utiliser des frameworks CSS** : Simplifiez le développement avec des frameworks comme Bootstrap ou Tailwind CSS.

---

## Liens utiles

- [Documentation officielle SCSS](https://sass-lang.com/documentation)
- [Tutoriels SCSS](https://www.w3schools.com/sass/)
- [Exemples de projets SCSS](https://github.com/sass/sass)
- [Documentation Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Documentation Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
