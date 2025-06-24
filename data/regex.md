# 📦 Regex

## Introduction

Les expressions régulières (Regex) sont des motifs utilisés pour rechercher, manipuler ou valider des chaînes de caractères. Elles sont puissantes et largement utilisées dans les langages de programmation pour le traitement de texte.

---

## Commandes essentielles

### Syntaxe de base

```regex
^abc       # Correspond à une chaîne qui commence par "abc"
abc$       # Correspond à une chaîne qui se termine par "abc"
\d+        # Correspond à un ou plusieurs chiffres
[a-z]      # Correspond à une lettre minuscule
[A-Z]      # Correspond à une lettre majuscule
\w+        # Correspond à un ou plusieurs caractères alphanumériques
\s         # Correspond à un espace
```

### Modificateurs

```regex
/i         # Ignore la casse
/g         # Recherche globale (toutes les occurrences)
/m         # Recherche multilignes
```

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

---

## Bonnes pratiques

1. **Utiliser des outils de test Regex** : Testez vos expressions régulières avec des outils comme [Regex101](https://regex101.com/) ou [RegExr](https://regexr.com/).
2. **Documenter les Regex complexes** : Ajoutez des commentaires pour expliquer les motifs complexes.
3. **Limiter les performances** : Évitez les motifs trop gourmands qui peuvent ralentir les traitements.

---

## Liens utiles

- [Documentation officielle Regex](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)
- [Tutoriels Regex](https://www.w3schools.com/jsref/jsref_obj_regexp.asp)
- [Outils de test Regex](https://regex101.com/)
