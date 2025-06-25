# 📦 Tiptap

## Introduction

Tiptap est un éditeur de texte riche basé sur ProseMirror. Il est conçu pour être extensible, personnalisable, et facile à intégrer dans des projets modernes. Tiptap est particulièrement adapté aux applications web nécessitant un éditeur de texte riche avec des fonctionnalités avancées comme les mentions, les tableaux, et les extensions personnalisées.

---

## Concepts clés

### Extensions

Les extensions sont des modules qui ajoutent des fonctionnalités à Tiptap. Par exemple, le StarterKit inclut des extensions de base comme les paragraphes, les listes, et les liens.

### Gestion des états

Tiptap permet de vérifier et de modifier l'état de l'éditeur, comme savoir si un style est actif ou appliquer des transformations au contenu.

### Intégration avec des frameworks

Tiptap est compatible avec Vue.js, React, et Vanilla JavaScript, ce qui le rend facile à intégrer dans des projets modernes.

---

## Pourquoi utiliser Tiptap ?

1. **Extensibilité** : Tiptap permet d'ajouter des extensions pour personnaliser l'éditeur.
2. **Compatibilité** : Fonctionne avec Vue.js, React, et Vanilla JavaScript.
3. **Personnalisation** : Permet de définir des menus, des barres d'outils, et des comportements spécifiques.
4. **Support des fonctionnalités avancées** : Gestion des tableaux, mentions, images, et bien plus.

---

## Installation

### Étapes pour installer Tiptap avec Vue.js

1. Installez les dépendances nécessaires :

```bash
npm install @tiptap/vue-3 @tiptap/core @tiptap/extension-starter-kit
```

2. Ajoutez Tiptap à votre projet Vue.js :

```javascript
// filepath: src/components/Editor.vue
<template>
  <div>
    <editor-content :editor="editor" />
  </div>
</template>

<script>
import { EditorContent, useEditor } from '@tiptap/vue-3';
import StarterKit from '@tiptap/extension-starter-kit';

export default {
  components: {
    EditorContent,
  },
  setup() {
    const editor = useEditor({
      extensions: [StarterKit],
      content: '<p>Écrivez ici...</p>',
    });

    return {
      editor,
    };
  },
};
</script>
```

---

## Extensions populaires

### StarterKit

Le StarterKit inclut les extensions de base comme les paragraphes, les titres, les listes, et les liens.

```javascript
import StarterKit from '@tiptap/extension-starter-kit';

const editor = useEditor({
  extensions: [StarterKit],
});
```

### Tableaux

Ajoutez la gestion des tableaux avec l'extension `@tiptap/extension-table`.

```bash
npm install @tiptap/extension-table
```

```javascript
import Table from '@tiptap/extension-table';
import TableRow from '@tiptap/extension-table-row';
import TableCell from '@tiptap/extension-table-cell';
import TableHeader from '@tiptap/extension-table-header';

const editor = useEditor({
  extensions: [
    StarterKit,
    Table.configure({
      resizable: true,
    }),
    TableRow,
    TableCell,
    TableHeader,
  ],
});
```

### Mentions

Ajoutez les mentions avec l'extension `@tiptap/extension-mention`.

```bash
npm install @tiptap/extension-mention
```

```javascript
import Mention from '@tiptap/extension-mention';

const editor = useEditor({
  extensions: [
    StarterKit,
    Mention.configure({
      HTMLAttributes: {
        class: 'mention',
      },
    }),
  ],
});
```

---

## Commandes utiles

### Manipuler le contenu

#### Ajouter du contenu

```javascript
editor.chain().focus().insertContent('<p>Nouveau contenu</p>').run();
```

#### Appliquer un style

```javascript
editor.chain().focus().toggleBold().run();
```

#### Supprimer du contenu

```javascript
editor.chain().focus().deleteRange({ from: 1, to: 5 }).run();
```

### Gérer les extensions

#### Ajouter une extension

```javascript
import CustomExtension from '@tiptap/extension-custom';

const editor = useEditor({
  extensions: [StarterKit, CustomExtension],
});
```

#### Configurer une extension

```javascript
import Table from '@tiptap/extension-table';

const editor = useEditor({
  extensions: [
    Table.configure({
      resizable: true,
    }),
  ],
});
```

### Vérifier l'état

#### Vérifier si un style est actif

```javascript
console.log(editor.isActive('bold')); // true ou false
```

#### Obtenir le contenu actuel

```javascript
console.log(editor.getHTML());
```

### Détruire l'éditeur

```javascript
editor.destroy();
```

---

## Informations pratiques

### Cas d'utilisation

1. **Éditeurs de blogs** : Implémentez Tiptap pour permettre aux utilisateurs de rédiger des articles avec des styles riches.

2. **Applications collaboratives** : Utilisez Tiptap pour créer des éditeurs collaboratifs avec des fonctionnalités comme les mentions et les tableaux.

3. **Personnalisation avancée** : Ajoutez des extensions personnalisées pour répondre aux besoins spécifiques de votre projet.

### Exemples avancés

#### Gestion des images

Ajoutez la gestion des images avec l'extension `@tiptap/extension-image`.

```bash
npm install @tiptap/extension-image
```

```javascript
import Image from '@tiptap/extension-image';

const editor = useEditor({
  extensions: [StarterKit, Image],
});
```

#### Gestion des couleurs

Ajoutez la gestion des couleurs avec l'extension `@tiptap/extension-color`.

```bash
npm install @tiptap/extension-color
```

```javascript
import Color from '@tiptap/extension-color';

const editor = useEditor({
  extensions: [StarterKit, Color],
});
```

---

## Bonnes pratiques enrichies

1. **Utiliser StarterKit** : Commencez avec StarterKit pour inclure les extensions de base.

2. **Personnaliser les extensions** : Configurez les extensions pour répondre aux besoins spécifiques de votre projet.

3. **Gérer les événements** : Ajoutez des écouteurs d'événements pour surveiller les changements dans l'éditeur.

4. **Optimiser les performances** : Chargez uniquement les extensions nécessaires pour réduire la taille du bundle.

5. **Tester les fonctionnalités** : Vérifiez les comportements des extensions dans différents scénarios.

6. **Documenter les extensions** : Ajoutez des commentaires pour expliquer les configurations et les comportements des extensions.

7. **Sécuriser les entrées utilisateur** : Validez et nettoyez les données avant de les enregistrer ou de les afficher.

---

## Liens utiles

- [Documentation officielle Tiptap](https://tiptap.dev/)

- [Extensions Tiptap](https://tiptap.dev/extensions)

- [Tutoriels Tiptap](https://tiptap.dev/guide/introduction)

- [ProseMirror](https://prosemirror.net/)
