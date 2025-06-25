# 📦 DTO (Data Transfer Object)

## Introduction

Les DTO (Data Transfer Objects) sont des objets utilisés pour transférer des données entre différentes couches d'une application. Ils permettent de structurer les données de manière claire et de réduire les dépendances entre les couches. Les DTO sont particulièrement utiles dans les architectures en couches, comme les applications web ou les microservices.

---

## Concepts clés

### Pourquoi utiliser des DTO ?

1. **Isolation des couches** : Les DTO permettent de découpler les couches de l'application (ex. frontend, backend, base de données), réduisant les dépendances directes.
2. **Validation des données** : Les DTO peuvent inclure des règles de validation pour garantir l'intégrité des données avant leur traitement.
3. **Optimisation des transferts** : Les DTO permettent de transférer uniquement les données nécessaires, réduisant la surcharge réseau.
4. **Standardisation** : Les DTO offrent une structure uniforme pour les données échangées entre les services.

### Enjeux pour les développeurs

1. **Clarté** : Les DTO doivent être bien définis pour éviter les ambiguïtés dans les données échangées.
2. **Validation** : Implémentez des mécanismes de validation pour garantir la qualité des données avant leur traitement.
3. **Maintenance** : Les DTO doivent être mis à jour lorsque les besoins de l'application évoluent, tout en maintenant la compatibilité avec les services existants.
4. **Conversion** : Les DTO doivent être convertis en entités ou objets métiers avant leur utilisation dans la logique métier.

---

## Commandes utiles

### TypeScript avec Nest.js

```bash
npm install class-validator class-transformer # Installe les outils de validation pour les DTO
```

---

## Exemples pratiques

### Exemple de DTO en TypeScript

```typescript
// filepath: src/dto/user.dto.ts
export class UserDTO {
  id: number;
  name: string;
  email: string;
  isActive: boolean;
}
```

### Exemple de DTO avec validation (Nest.js)

```typescript
// filepath: src/dto/create-user.dto.ts
import { IsEmail, IsNotEmpty, IsBoolean } from 'class-validator';

export class CreateUserDTO {
  @IsNotEmpty()
  name: string;

  @IsEmail()
  email: string;

  @IsBoolean()
  isActive: boolean;
}
```

### Conversion entre entités et DTO

```typescript
// filepath: src/utils/mapper.ts
import { User } from '../entity/user.entity';
import { UserDTO } from '../dto/user.dto';

export function toUserDTO(user: User): UserDTO {
  return {
    id: user.id,
    name: user.name,
    email: user.email,
    isActive: user.isActive,
  };
}
```

---

## Bonnes pratiques

1. **Utiliser des bibliothèques de validation** : Intégrez des outils comme `class-validator` pour valider les DTO avant leur traitement.
2. **Documenter les DTO** : Ajoutez des commentaires pour expliquer les propriétés et leur usage, facilitant la compréhension par les autres développeurs.
3. **Limiter les dépendances** : Les DTO doivent être indépendants des entités de base de données pour éviter les couplages excessifs.
4. **Automatiser la conversion** : Utilisez des outils ou des fonctions pour convertir les entités en DTO et vice versa.
5. **Versionner les DTO** : Dans les applications évolutives, versionnez les DTO pour gérer les changements sans casser les services existants.

---

## Outils utiles

- **Class-validator** : Validation des DTO dans les projets TypeScript/Nest.js.
- **Class-transformer** : Transformation des objets en DTO et vice versa.
- **Swagger** : Génération automatique de documentation pour les DTO dans les API.
- **MapStruct** : Outil de mapping pour les DTO dans les projets Java.

---

## Liens utiles

- [Documentation Nest.js DTO](https://docs.nestjs.com/controllers#request-payloads)
- [Class-validator](https://github.com/typestack/class-validator)
- [Class-transformer](https://github.com/typestack/class-transformer)
- [Swagger pour Nest.js](https://docs.nestjs.com/openapi/introduction)
