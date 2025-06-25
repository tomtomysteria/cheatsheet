# 📦 Regex

## Introduction

Les expressions régulières (Regex) sont des motifs utilisés pour rechercher, manipuler ou valider des chaînes de caractères. Elles sont puissantes et largement utilisées dans les langages de programmation pour le traitement de texte. Regex est un outil essentiel pour les développeurs travaillant sur des tâches comme la validation de formulaires, l'extraction de données, ou le nettoyage de texte.

---

## Concepts clés

### Pourquoi utiliser Regex ?

1. **Validation** : Vérifiez que les données respectent un format spécifique (ex. email, mot de passe, numéro de téléphone).
2. **Recherche et extraction** : Identifiez et récupérez des motifs spécifiques dans des chaînes de caractères.
3. **Manipulation** : Modifiez ou remplacez des parties de texte en fonction de motifs définis.

### Enjeux pour les développeurs

1. **Complexité** : Les Regex peuvent devenir difficiles à lire et à maintenir, surtout pour les motifs complexes.
2. **Performance** : Les motifs gourmands peuvent ralentir les traitements, surtout sur de grandes chaînes.
3. **Portabilité** : Les implémentations Regex peuvent varier légèrement entre les langages de programmation.

---

## Syntaxe de base

### Caractères spéciaux

- `.` : Correspond à n'importe quel caractère sauf un saut de ligne.
- `^` : Correspond au début de la chaîne.
- `$` : Correspond à la fin de la chaîne.
- `\` : Échappe un caractère spécial (ex. `\.` pour correspondre à un point).

### Classes de caractères

- `\d` : Correspond à un chiffre (0-9).
- `\w` : Correspond à un caractère alphanumérique (lettres, chiffres, ou `_`).
- `\s` : Correspond à un espace blanc (espace, tabulation, etc.).
- `[abc]` : Correspond à un caractère parmi `a`, `b`, ou `c`.
- `[a-z]` : Correspond à une lettre minuscule.
- `[A-Z]` : Correspond à une lettre majuscule.

### Quantificateurs

- `*` : Correspond à 0 ou plusieurs occurrences.
- `+` : Correspond à 1 ou plusieurs occurrences.
- `?` : Correspond à 0 ou 1 occurrence.
- `{n}` : Correspond exactement à `n` occurrences.
- `{n,}` : Correspond à `n` occurrences ou plus.
- `{n,m}` : Correspond entre `n` et `m` occurrences.

---

## Modificateurs

Les modificateurs permettent de changer le comportement des Regex :

- `/i` : Ignore la casse.
- `/g` : Recherche globale (toutes les occurrences).
- `/m` : Recherche multilignes.

---

## Exemples pratiques

### Validation d'une adresse email

```javascript
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
console.log(emailRegex.test("example@example.com")); // true
```

### Extraction des numéros de téléphone

```javascript
const text = "Contactez-nous au 06-12345678 ou au 07-87654321.";
const phoneRegex = /\b\d{2}-\d{8}\b/g;
console.log(text.match(phoneRegex)); // ["06-12345678", "07-87654321"]
```

### Remplacement de texte

```javascript
const text = "Bonjour, monde!";
const replacedText = text.replace(/monde/, "Regex");
console.log(replacedText); // "Bonjour, Regex!"
```

### Validation d'un mot de passe

```javascript
const passwordRegex = /^(?=.*[A-Z])(?=.*[a-z])(?=.*\d).{8,}$/;
console.log(passwordRegex.test("Password123")); // true
```

### Extraction des URLs

```javascript
const text = "Visitez https://example.com ou http://test.com.";
const urlRegex = /https?:\/\/[^\s]+/g;
console.log(text.match(urlRegex)); // ["https://example.com", "http://test.com"]
```

---

## Bonnes pratiques

1. **Utiliser des outils de test Regex** : Testez vos expressions régulières avec des outils comme [Regex101](https://regex101.com/) ou [RegExr](https://regexr.com/).
2. **Documenter les Regex complexes** : Ajoutez des commentaires pour expliquer les motifs complexes.
3. **Limiter les performances** : Évitez les motifs trop gourmands qui peuvent ralentir les traitements.
4. **Modulariser les Regex** : Divisez les motifs complexes en parties plus simples et réutilisables.
5. **Valider les entrées utilisateur** : Combinez Regex avec des validations supplémentaires pour éviter les abus.

---

## Outils utiles

1. **Éditeurs en ligne** :
   - [Regex101](https://regex101.com/) : Testez vos expressions régulières avec des explications détaillées.
   - [RegExr](https://regexr.com/) : Interface intuitive pour tester et apprendre les Regex.

2. **Linting Regex** :
   - Utilisez des outils comme `eslint-plugin-regex` pour vérifier la qualité des expressions régulières dans votre code.

3. **Bibliothèques populaires** :
   - **JavaScript** : `RegExp` intégré.
   - **Python** : Module `re`.
   - **Java** : Classe `Pattern`.

---

## Liens utiles

- [Documentation officielle Regex](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)
- [Tutoriels Regex](https://www.w3schools.com/jsref/jsref_obj_regexp.asp)
- [Outils de test Regex](https://regex101.com/)
- [Regex Cheatsheet](https://www.debuggex.com/cheatsheet/regex/javascript)
