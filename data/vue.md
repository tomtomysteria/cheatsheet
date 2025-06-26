# Vue.js

## Introduction

Vue.js est un framework JavaScript progressif pour construire des interfaces utilisateur. Il est conçu pour être simple à utiliser et facile à intégrer dans des projets existants. Vue.js offre une architecture basée sur les composants et un système réactif puissant.

## Concepts clés

### Composants

Les composants sont les blocs de construction de base d'une application Vue.js. Chaque composant est constitué de :

- Un template HTML.

- Une logique JavaScript.

- Un style CSS ou SCSS.

Exemple de composant :

```vue
<template>
  <div>
    <h1>{{ message }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello Vue.js!'
    };
  }
};
</script>

<style>
h1 {
  color: blue;
}
</style>
```

### Directives

Les directives sont des attributs spéciaux dans Vue.js qui permettent de manipuler le DOM. Exemples :

- `v-if` : Affiche un élément conditionnellement.

- `v-for` : Itère sur une liste.

- `v-bind` : Lie des attributs dynamiquement.

Exemple de directive :

```vue
<template>
  <ul>
    <li v-for="item in items" :key="item.id">{{ item.name }}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { id: 1, name: 'Item 1' },
        { id: 2, name: 'Item 2' }
      ]
    };
  }
};
</script>
```

### Routage

Vue.js utilise `vue-router` pour gérer la navigation entre les pages.

Exemple de configuration de routage :

```javascript
import { createRouter, createWebHistory } from 'vue-router';
import Home from './components/Home.vue';
import About from './components/About.vue';

const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About }
];

const router = createRouter({
  history: createWebHistory(),
  routes
});

export default router;
```

### Gestion d'état

Vue.js propose `Vuex` pour gérer l'état global de l'application.

Exemple de store Vuex :

```javascript
import { createStore } from 'vuex';

const store = createStore({
  state() {
    return {
      count: 0
    };
  },
  mutations: {
    increment(state) {
      state.count++;
    }
  }
});

export default store;
```

### Tests

Vue.js peut être testé avec des outils comme `Jest` ou `Vue Test Utils`.

Exemple de test avec Jest :

```javascript
import { mount } from '@vue/test-utils';
import MyComponent from './MyComponent.vue';

describe('MyComponent', () => {
  it('renders the correct message', () => {
    const wrapper = mount(MyComponent);
    expect(wrapper.text()).toContain('Hello Vue.js!');
  });
});
```

### Logs

Pour gérer les logs dans une application Vue.js, vous pouvez utiliser des bibliothèques comme `loglevel`.

Exemple de configuration de logs :

```javascript
import log from 'loglevel';

log.setLevel('info');
log.info('This is an info log');
log.error('This is an error log');
```

## Installation

Pour installer Vue.js, utilisez la commande suivante :

```bash
npm install vue
```

## Commandes principales

- `vue create <nom-du-projet>` : Crée un nouveau projet Vue.js.

- `npm run serve` : Démarre le serveur de développement.

- `npm run build` : Compile le projet pour la production.

- `npm run test` : Exécute les tests unitaires.

## Structure du projet

- `src/components` : Contient les composants Vue.

- `src/assets` : Contient les fichiers statiques comme les images.

- `src/router` : Contient les configurations de routage.

- `src/store` : Contient la gestion d'état avec Vuex.

## Documentation officielle

[Vue.js Documentation](https://vuejs.org/v2/guide/)
