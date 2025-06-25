# 📦 Zod

## Introduction

Zod est une bibliothèque TypeScript pour la validation et la gestion des schémas. Elle permet de définir des schémas de données, de valider les entrées, et de générer des types TypeScript basés sur ces schémas. Zod est particulièrement utile pour les applications modernes où la validation des données est essentielle.

---

## Pourquoi utiliser Zod ?

1. **Validation robuste** : Zod offre une validation puissante et flexible pour les données.
2. **Types TypeScript** : Génère automatiquement des types TypeScript basés sur les schémas définis.
3. **Facilité d'utilisation** : Syntaxe intuitive pour définir des schémas et valider les données.
4. **Interopérabilité** : Fonctionne parfaitement avec des frameworks comme React, Next.js, et Express.

---

## Installation

### Étapes pour installer Zod

1. Installez Zod dans votre projet :

```bash
npm install zod
```

2. Ajoutez les types TypeScript si nécessaire :

```bash
npm install --save-dev @types/zod
```

---

## Utilisation

### Définir un schéma

```typescript
import { z } from 'zod';

const userSchema = z.object({
  id: z.number(),
  name: z.string(),
  email: z.string().email(),
  isActive: z.boolean(),
});
```

### Valider des données

```typescript
const userData = {
  id: 1,
  name: 'Alice',
  email: 'alice@example.com',
  isActive: true,
};

const result = userSchema.safeParse(userData);

if (result.success) {
  console.log('Données valides :', result.data);
} else {
  console.error('Erreurs de validation :', result.error.errors);
}
```

### Générer des types TypeScript

```typescript
type User = z.infer<typeof userSchema>;

const user: User = {
  id: 1,
  name: 'Alice',
  email: 'alice@example.com',
  isActive: true,
};
```

---

## Schémas avancés

### Schéma avec des valeurs par défaut

```typescript
const userSchema = z.object({
  id: z.number(),
  name: z.string(),
  isActive: z.boolean().default(true),
});
```

### Schéma avec des tableaux

```typescript
const userListSchema = z.array(
  z.object({
    id: z.number(),
    name: z.string(),
  })
);
```

### Schéma avec des unions

```typescript
const statusSchema = z.union([z.literal('active'), z.literal('inactive')]);

const userSchema = z.object({
  id: z.number(),
  status: statusSchema,
});
```

### Schéma avec des enums

```typescript
const roleSchema = z.enum(['admin', 'user', 'guest']);

const userSchema = z.object({
  id: z.number(),
  role: roleSchema,
});
```

---

## Intégration avec Express

### Exemple de middleware pour valider les requêtes

```typescript
import express from 'express';
import { z } from 'zod';

const app = express();
app.use(express.json());

const userSchema = z.object({
  id: z.number(),
  name: z.string(),
  email: z.string().email(),
});

app.post('/users', (req, res) => {
  const result = userSchema.safeParse(req.body);

  if (!result.success) {
    return res.status(400).json({ errors: result.error.errors });
  }

  res.status(201).json({ user: result.data });
});

app.listen(3000, () => console.log('Serveur démarré sur le port 3000'));
```

---

## Bonnes pratiques

1. **Centraliser les schémas** : Regroupez les schémas dans un dossier dédié pour faciliter la gestion.
2. **Utiliser `safeParse`** : Préférez `safeParse` pour éviter les exceptions lors de la validation.
3. **Documenter les schémas** : Ajoutez des commentaires pour expliquer les règles de validation.
4. **Combiner avec TypeScript** : Utilisez `z.infer` pour générer des types TypeScript basés sur les schémas.
5. **Valider les entrées utilisateur** : Implémentez des schémas pour valider les données des formulaires et des API.

---

## Liens utiles

- [Documentation officielle Zod](https://zod.dev/)
- [Tutoriels Zod](https://www.tutorialspoint.com/zod/index.htm)
- [Exemples de projets Zod](https://github.com/colinhacks/zod)
- [Zod avec TypeScript](https://typescriptlang.org/docs/)
