# 📦 React

## Introduction

React est une bibliothèque JavaScript développée par Facebook pour créer des interfaces utilisateur interactives. Elle permet de construire des composants réutilisables et de gérer efficacement l'état des applications. React est idéal pour les applications web modernes nécessitant une expérience utilisateur fluide et dynamique. Grâce à son approche déclarative, React simplifie la création d'interfaces complexes tout en offrant des performances optimales.

---

## Commandes essentielles

### React CLI

```bash
npx create-react-app my-app           # Crée un nouveau projet React
npm start                             # Démarre le serveur de développement
npm run build                         # Compile le projet pour la production
npm test                              # Exécute les tests
npm run eject                         # Extrait la configuration de Create React App
npm install <package>                 # Installe un package
npm uninstall <package>               # Supprime un package
npm audit                             # Analyse les vulnérabilités des dépendances
npm cache clean --force               # Nettoie le cache NPM
npm list                              # Liste les dépendances installées
npm outdated                          # Liste les packages obsolètes
```

---

## Concepts clés

### Composants

#### Exemple de composant fonctionnel

```javascript
// filepath: components/Button.js
export default function Button({ label, onClick }) {
    return <button onClick={onClick}>{label}</button>;
}
```

#### Exemple de composant avec état

```javascript
// filepath: components/Counter.js
import { useState } from 'react';

export default function Counter() {
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

## Hooks

### Exemple d'utilisation de `useEffect`

```javascript
// filepath: components/EffectExample.js
import { useEffect, useState } from 'react';

export default function EffectExample() {
    const [data, setData] = useState(null);

    useEffect(() => {
        fetch('https://api.example.com/data')
            .then((response) => response.json())
            .then((data) => setData(data));
    }, []);

    return <pre>{JSON.stringify(data, null, 2)}</pre>;
}
```

### Exemple d'utilisation de `useContext`

```javascript
// filepath: context/ThemeContext.js
import { createContext, useContext } from 'react';

const ThemeContext = createContext('light');

export function useTheme() {
    return useContext(ThemeContext);
}

export function ThemeProvider({ children }) {
    return <ThemeContext.Provider value="dark">{children}</ThemeContext.Provider>;
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

## Tests avec React

### Utilisation de Jest et React Testing Library

Ajoutez les dépendances au projet :

```bash
npm install --save-dev @testing-library/react @testing-library/jest-dom
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
npm test
```

---

## Gestion des logs

### Utilisation de `console`

```javascript
// filepath: utils/logger.js
export function logInfo(message) {
    console.log(`Info : ${message}`);
}

export function logWarn(message) {
    console.warn(`Avertissement : ${message}`);
}

export function logError(message) {
    console.error(`Erreur : ${message}`);
}
```

---

## Bonnes pratiques

1. **Structurer les projets** : Organisez les fichiers en dossiers (ex. `components`, `hooks`, `context`, `services`, `models`, `utils`) pour améliorer la maintenabilité.
2. **Utiliser les hooks** : Simplifiez la gestion des états et des effets avec `useState`, `useEffect`, et autres hooks React.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
4. **Activer les logs** : Utilisez `console` ou des bibliothèques comme `winston` pour surveiller les performances et les erreurs.
5. **Optimiser les performances** : Utilisez `React.memo` pour éviter les rendus inutiles.
6. **Configurer les environnements** : Utilisez des fichiers `.env` pour gérer les variables d'environnement.
7. **Utiliser Context API** : Simplifiez le partage de données entre composants avec `useContext`.
8. **Utiliser des services** : Centralisez les appels API dans des services pour améliorer la maintenabilité.

---

## Liens utiles

- [Documentation officielle React](https://reactjs.org/docs/getting-started.html)
- [Tutoriels React](https://reactjs.org/tutorial/tutorial.html)
- [Exemples de projets React](https://github.com/facebook/react/tree/main/examples)
- [Documentation React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
