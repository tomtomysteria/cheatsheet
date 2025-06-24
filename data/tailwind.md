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

## Exemples pratiques

### Exemple de fichier `tailwind.config.js`

Personnalisez Tailwind CSS en modifiant le fichier de configuration :

```javascript
module.exports = {
  content: ['./src/**/*.{html,js}'],
  theme: {
    extend: {
      colors: {
        primary: '#3498db',
        secondary: '#2ecc71',
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

---

## Liens utiles

- [Documentation officielle Tailwind CSS](https://tailwindcss.com/docs)
- [Tutoriels Tailwind CSS](https://tailwindcss.com/docs/installation)
- [Exemples de projets Tailwind CSS](https://github.com/tailwindlabs/tailwindcss-examples)
