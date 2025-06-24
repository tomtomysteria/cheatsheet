# 📦 React

## Introduction

React est une bibliothèque JavaScript développée par Facebook pour construire des interfaces utilisateur dynamiques et réactives. Elle est basée sur le concept de composants et utilise un DOM virtuel pour optimiser les performances.

---

## Commandes essentielles

### Installation et création de projet

```bash
npx create-react-app my-app           # Crée un nouveau projet React
npm start                             # Démarre l'application en mode développement
npm run build                         # Génère une version optimisée pour la production
npm test                              # Exécute les tests
```

### Gestion des dépendances

```bash
npm install react-router-dom          # Installe React Router pour la navigation
npm install axios                     # Installe Axios pour les requêtes HTTP
```

---

## Exemples pratiques

### Exemple de composant fonctionnel

```javascript
import React from 'react';

function App() {
  return <h1>Hello, React!</h1>;
}

export default App;
```

### Utilisation des hooks

#### Hook `useState`

```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default Counter;
```

#### Hook `useEffect`

```javascript
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []);

  return (
    <ul>
      {data.map((item) => (
        <li key={item.id}>{item.title}</li>
      ))}
    </ul>
  );
}

export default DataFetcher;
```

### Utilisation de React Router

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

function Home() {
  return <h1>Home Page</h1>;
}

function About() {
  return <h1>About Page</h1>;
}

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/" exact component={Home} />
        <Route path="/about" component={About} />
      </Switch>
    </Router>
  );
}

export default App;
```

---

## Bonnes pratiques

1. **Structurer les fichiers** : Organisez votre projet avec des dossiers comme `components`, `pages`, et `hooks` pour une meilleure maintenabilité.
2. **Utiliser les PropTypes** : Validez les props des composants avec `prop-types`.

   ```bash
   npm install prop-types
   ```

   Exemple :

   ```javascript
   import PropTypes from 'prop-types';

   function Greeting({ name }) {
     return <h1>Hello, {name}!</h1>;
   }

   Greeting.propTypes = {
     name: PropTypes.string.isRequired,
   };

   export default Greeting;
   ```

3. **Optimiser les performances** : Utilisez `React.memo` pour éviter les rendus inutiles des composants.

---

## Liens utiles

- [Documentation officielle React](https://reactjs.org)
- [Tutoriels React](https://reactjs.org/tutorial/tutorial.html)
- [Exemples de projets React](https://github.com/facebook/react/tree/main/examples)
