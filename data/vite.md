# Vite

## Introduction

Vite est un outil de construction rapide pour les projets web modernes. Il est conçu pour offrir une expérience de développement rapide et efficace. Vite utilise une approche basée sur les modules ES et offre un temps de démarrage quasi instantané pour les projets.

## Concepts clés

### Modules ES

Vite utilise les modules ES natifs du navigateur pour charger les fichiers JavaScript, ce qui élimine le besoin de bundling pendant le développement.

#### Exemple

```javascript
// Exemple de module ES
export function greet(name) {
  return `Hello, ${name}!`;
}
```

### Hot Module Replacement (HMR)

Vite offre un système de remplacement à chaud des modules, permettant de mettre à jour les fichiers sans recharger la page.

#### Exemple

```javascript
// Exemple de HMR
if (import.meta.hot) {
  import.meta.hot.accept((newModule) => {
    // Remplacez le module par le nouveau contenu
  });
}
```

### Build Optimisé

Vite utilise `Rollup` pour la compilation des fichiers en production, garantissant des performances optimales.

#### Exemple

```javascript
// Configuration de build optimisé dans vite.config.js
export default defineConfig({
  build: {
    rollupOptions: {
      output: {
        manualChunks(id) {
          if (id.includes('node_modules')) {
            return id.toString().split('node_modules/')[1].split('/')[0].toString();
          }
        }
      }
    }
  }
});
```

## Installation

Pour installer Vite, utilisez la commande suivante :

```bash
npm create vite@latest
```

## Commandes principales

- `npm run dev` : Démarre le serveur de développement.

- `npm run build` : Compile le projet pour la production.

- `npm run preview` : Prévisualise le projet compilé.

- `vite` : Exécute Vite directement.

- `vite build` : Lance une compilation manuelle.

- `vite preview` : Prévisualise le projet compilé.

## Structure du projet

- `src` : Contient les fichiers source de l'application.
  - `main.js` ou `main.ts` : Point d'entrée de l'application.
  - `components/` : Contient les composants réutilisables.

- `public` : Contient les fichiers statiques accessibles directement.

- `vite.config.js` ou `vite.config.ts` : Fichier de configuration de Vite.

## Configuration

Exemple de configuration de Vite :

```javascript
import { defineConfig } from 'vite';
import vue from '@vitejs/plugin-vue';

export default defineConfig({
  plugins: [vue()],
  server: {
    port: 3000,
    open: true
  },
  build: {
    outDir: 'dist',
    sourcemap: true
  }
});
```

## Bonnes pratiques

- Utilisez des plugins pour étendre les fonctionnalités de Vite (ex : `@vitejs/plugin-vue` pour Vue).

- Configurez le cache pour optimiser les performances.

- Utilisez le mode `production` pour les builds.

- Testez votre application avec des outils comme `Vitest`.

## Tests

Vite peut être utilisé avec des outils comme `Vitest` pour les tests unitaires.

Exemple de test avec Vitest :

```javascript
import { describe, it, expect } from 'vitest';

describe('Example Test', () => {
  it('should pass', () => {
    expect(true).toBe(true);
  });
});
```

## Logs

Pour gérer les logs dans une application utilisant Vite, vous pouvez intégrer des bibliothèques comme `winston` ou `loglevel`.

Exemple de configuration de logs avec `loglevel` :

```javascript
import log from 'loglevel';

log.setLevel('info');
log.info('This is an info log');
log.error('This is an error log');
```

## Documentation officielle

[Vite Documentation](https://vitejs.dev/guide/)
