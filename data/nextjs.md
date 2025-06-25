# 📦 Next.js

## Introduction

Next.js est un framework React qui permet de créer des applications web modernes avec rendu côté serveur (SSR), génération statique (SSG), et rendu côté client (CSR). Il simplifie le développement grâce à ses fonctionnalités intégrées comme les routes automatiques, les API routes, et l'optimisation des performances. Next.js est idéal pour les applications nécessitant une haute performance, une SEO optimisée, et une expérience utilisateur fluide.

---

## Commandes essentielles

### Next.js CLI

```bash
npx create-next-app@latest my-app       # Crée un nouveau projet Next.js
npm run dev                             # Démarre le serveur de développement
npm run build                           # Compile le projet pour la production
npm run start                           # Démarre le serveur en mode production
npm run lint                            # Analyse le code pour détecter les erreurs
npm run test                            # Exécute les tests
npm run export                          # Génère une version statique du site
```

---

## Concepts clés

### Pages et routage automatique

#### Exemple de page

```javascript
// filepath: pages/index.js
export default function Home() {
    return (
        <div>
            <h1>Bienvenue dans Next.js</h1>
        </div>
    );
}
```

#### Exemple de page dynamique

```javascript
// filepath: pages/product/[id].js
import { useRouter } from 'next/router';

export default function Product() {
    const router = useRouter();
    const { id } = router.query;

    return <h1>Produit ID : {id}</h1>;
}
```

---

## Rendu côté serveur (SSR)

Next.js permet de générer des pages dynamiques côté serveur.

#### Exemple de SSR avec `getServerSideProps`

```javascript
// filepath: pages/ssr-example.js
export async function getServerSideProps() {
    const data = await fetch('https://api.example.com/data').then(res => res.json());
    return { props: { data } };
}

export default function SSRExample({ data }) {
    return (
        <div>
            <h1>Données côté serveur</h1>
            <pre>{JSON.stringify(data, null, 2)}</pre>
        </div>
    );
}
```

---

## Génération statique (SSG)

Next.js permet de générer des pages statiques au moment de la construction.

#### Exemple de SSG avec `getStaticProps`

```javascript
// filepath: pages/ssg-example.js
export async function getStaticProps() {
    const data = await fetch('https://api.example.com/data').then(res => res.json());
    return { props: { data } };
}

export default function SSGExample({ data }) {
    return (
        <div>
            <h1>Données statiques</h1>
            <pre>{JSON.stringify(data, null, 2)}</pre>
        </div>
    );
}
```

---

## API Routes

Next.js permet de créer des API directement dans le projet.

#### Exemple d'API route

```javascript
// filepath: pages/api/hello.js
export default function handler(req, res) {
    res.status(200).json({ message: 'Hello, API!' });
}
```

#### Exemple d'API avec méthode POST

```javascript
// filepath: pages/api/user.js
export default function handler(req, res) {
    if (req.method === 'POST') {
        const { name, email } = req.body;
        res.status(201).json({ id: 1, name, email });
    } else {
        res.status(405).json({ message: 'Méthode non autorisée' });
    }
}
```

---

## Composants et hooks

### Exemple de composant

```javascript
// filepath: components/Button.js
export default function Button({ label, onClick }) {
    return <button onClick={onClick}>{label}</button>;
}
```

### Exemple d'utilisation de hooks

```javascript
// filepath: pages/hooks-example.js
import { useState } from 'react';

export default function HooksExample() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Compteur : {count}</p>
            <button onClick={() => setCount(count + 1)}>Incrémenter</button>
        </div>
    );
}
```

---

## Services et modèles

### Exemple de service

```javascript
// filepath: services/userService.js
export async function fetchUser(id) {
    const response = await fetch(`/api/user/${id}`);
    return response.json();
}
```

### Exemple de modèle (DTO)

```javascript
// filepath: models/UserDTO.js
export class UserDTO {
    constructor(id, name, email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }
}
```

---

## Tests avec Next.js

### Utilisation de Jest

Ajoutez Jest au projet :

```bash
npm install --save-dev jest @testing-library/react @testing-library/jest-dom
```

#### Exemple de test

```javascript
// filepath: __tests__/Button.test.js
import { render, screen } from '@testing-library/react';
import Button from '../components/Button';

test('affiche le label du bouton', () => {
    render(<Button label="Cliquez ici" />);
    expect(screen.getByText('Cliquez ici')).toBeInTheDocument();
});
```

Exécutez les tests :

```bash
npm run test
```

---

## Gestion des logs

### Utilisation de `console`

```javascript
export default function LoggerExample() {
    console.log('Info : opération réussie');
    console.warn('Avertissement : attention à cette étape');
    console.error('Erreur : une exception est survenue');

    return <div>Voir les logs dans la console</div>;
}
```

---

## Bonnes pratiques

1. **Structurer les projets** : Organisez les fichiers en dossiers (ex. `pages`, `components`, `hooks`, `services`, `models`) pour améliorer la maintenabilité.
2. **Utiliser les API routes** : Implémentez des API simples directement dans le projet Next.js.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
4. **Activer les logs** : Utilisez `console` ou des bibliothèques comme `winston` pour surveiller les performances et les erreurs.
5. **Optimiser les images** : Utilisez le composant `next/image` pour gérer les images efficacement.
6. **Utiliser les hooks** : Simplifiez la gestion des états et des effets avec `useState`, `useEffect`, et autres hooks React.
7. **Configurer les environnements** : Utilisez des fichiers `.env.local` pour gérer les variables d'environnement.

---

## Liens utiles

- [Documentation officielle Next.js](https://nextjs.org/docs)
- [Tutoriels Next.js](https://nextjs.org/learn)
- [Exemples de projets Next.js](https://github.com/vercel/next.js/tree/canary/examples)
- [Documentation React](https://reactjs.org/docs/getting-started.html)
