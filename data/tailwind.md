# 📦 Tailwind CSS

## Introduction

Tailwind CSS est un framework CSS utilitaire qui permet de créer des designs rapidement et efficacement. Il offre une approche basée sur les classes utilitaires pour styliser directement les éléments HTML sans écrire de CSS personnalisé.

---

## Commandes essentielles

### Installation et configuration

```bash
npm install tailwindcss               # Installe Tailwind CSS
npx tailwindcss init                  # Génère un fichier de configuration `tailwind.config.js`
```

### Compilation des styles

```bash
npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch  # Compile les styles en mode veille
```

---

## Concepts clés

### Classes utilitaires

Tailwind CSS propose des classes utilitaires pour styliser les éléments HTML. Ces classes sont organisées par catégories :

- **Couleurs** : `bg-red-500`, `text-blue-700`
- **Espacement** : `p-4`, `m-2`
- **Flexbox** : `flex`, `justify-center`, `items-start`
- **Grille** : `grid`, `grid-cols-3`, `gap-4`
- **Typographie** : `font-bold`, `text-lg`, `leading-loose`

### Responsive Design

Tailwind CSS facilite la création de designs responsives grâce aux préfixes de breakpoints :

```html
<div class="text-sm md:text-lg lg:text-xl">
  Texte responsive
</div>
```

### Pseudo-classes

Utilisez des pseudo-classes pour styliser les états des éléments :

```html
<button class="bg-blue-500 hover:bg-blue-700 focus:ring-2 focus:ring-blue-300">
  Bouton stylisé
</button>
```

---

## Exemples pratiques

### Exemple de fichier `tailwind.config.js`

Personnalisez Tailwind CSS en modifiant le fichier de configuration :

```javascript
// filepath: ./tailwind.config.js
module.exports = {
  content: ['./src/**/*.{html,js}'],
  theme: {
    extend: {
      colors: {
        primary: '#3498db',
        secondary: '#2ecc71',
      },
      spacing: {
        '72': '18rem',
        '84': '21rem',
        '96': '24rem',
      },
    },
  },
  plugins: [],
};
```

### Utilisation des classes utilitaires

#### Mise en page

```html
<div class="flex justify-center items-center h-screen bg-gray-100">
  <div class="p-4 bg-white rounded shadow">
    Hello, Tailwind!
  </div>
</div>
```

#### Boutons stylisés

```html
<button class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">
  Cliquez ici
</button>
```

#### Grille responsive

```html
<div class="grid grid-cols-1 md:grid-cols-3 gap-4">
  <div class="bg-red-500 p-4">Colonne 1</div>
  <div class="bg-green-500 p-4">Colonne 2</div>
  <div class="bg-blue-500 p-4">Colonne 3</div>
</div>
```

---

## Plugins Tailwind CSS

### Installation de plugins

Ajoutez des plugins pour étendre les fonctionnalités de Tailwind CSS :

```bash
npm install @tailwindcss/forms @tailwindcss/typography
```

### Configuration des plugins

Activez les plugins dans le fichier `tailwind.config.js` :

```javascript
module.exports = {
  plugins: [
    require('@tailwindcss/forms'),
    require('@tailwindcss/typography'),
  ],
};
```

### Exemple avec le plugin Typography

```html
<article class="prose">
  <h1>Article avec typographie</h1>
  <p>Ce texte est stylisé avec le plugin Typography.</p>
</article>
```

---

## Bonnes pratiques

1. **Utiliser les classes utilitaires** : Exploitez les classes utilitaires pour éviter d'écrire du CSS personnalisé.
2. **Configurer le purge CSS** : Activez la purge des classes inutilisées pour réduire la taille des fichiers CSS en production.

   ```javascript
   module.exports = {
     content: ['./src/**/*.{html,js}'],
     theme: {
       extend: {},
     },
     plugins: [],
   };
   ```

3. **Personnaliser le thème** : Étendez le thème Tailwind pour ajouter vos propres couleurs, polices, et tailles.
4. **Utiliser les plugins** : Ajoutez des plugins pour enrichir les fonctionnalités de Tailwind CSS.

---

## Liens utiles

- [Documentation officielle Tailwind CSS](https://tailwindcss.com/docs)
- [Tutoriels Tailwind CSS](https://tailwindcss.com/docs/installation)
- [Exemples de projets Tailwind CSS](https://github.com/tailwindlabs/tailwindcss-examples)
