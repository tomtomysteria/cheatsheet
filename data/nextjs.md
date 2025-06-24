# 📦 Next.js

## Introduction

Next.js est un framework React puissant qui permet de créer des applications web modernes avec rendu côté serveur (SSR), génération statique (SSG), et API intégrées. Il est idéal pour les projets nécessitant des performances élevées et une SEO optimisée.

---

## Commandes essentielles

### Installation et gestion de projet

```bash
npx create-next-app my-app               # Crée un nouveau projet Next.js
npm run dev                              # Démarre l'application en mode développement
npm run build                            # Génère une version optimisée pour la production
npm run start                            # Démarre l'application en mode production
```

### Gestion des pages et API

```bash
mkdir pages                              # Crée un dossier pour les pages
mkdir pages/api                          # Crée un dossier pour les API
```

---

## Exemples pratiques

### Exemple de page avec rendu côté serveur (SSR)

```javascript
import React from 'react';

export async function getServerSideProps() {
  return {
    props: {
      message: 'Hello, SSR!',
    },
  };
}

export default function Home({ message }) {
  return <h1>{message}</h1>;
}
```

### Exemple de page avec génération statique (SSG)

```javascript
import React from 'react';

export async function getStaticProps() {
  return {
    props: {
      message: 'Hello, SSG!',
    },
  };
}

export default function Home({ message }) {
  return <h1>{message}</h1>;
}
```

### Exemple d'API intégrée

```javascript
export default function handler(req, res) {
  res.status(200).json({ message: 'Hello, API!' });
}
```

---

## Bonnes pratiques

1. **Utiliser les fonctionnalités avancées** : Exploitez les fonctionnalités comme `getServerSideProps` et `getStaticProps` pour optimiser le rendu des pages.
2. **Organiser les fichiers** : Structurez votre projet avec des dossiers comme `pages`, `components`, et `styles` pour une meilleure maintenabilité.
3. **Optimiser les performances** : Utilisez les images optimisées avec le composant `<Image>` de Next.js et configurez la mise en cache.

---

## Liens utiles

- [Documentation officielle Next.js](https://nextjs.org/docs)
- [Tutoriels Next.js](https://nextjs.org/learn)
- [Exemples de projets Next.js](https://github.com/vercel/next.js/tree/canary/examples)
