# 📦 Markdown

## Introduction

Markdown est un langage de balisage léger qui permet de formater du texte de manière simple et lisible. Il est largement utilisé pour la documentation, les blogs, les fichiers README, et bien plus encore.

---

## Syntaxe de base

### Titres
Utilisez `#` pour créer des titres :
```markdown
# Titre de niveau 1
## Titre de niveau 2
### Titre de niveau 3
```

### Texte
- **Gras** : `**texte**` ou `__texte__`
- *Italique* : `*texte*` ou `_texte_`
- ~~Barré~~ : `~~texte~~`

### Listes
- **Liste à puces** :
```markdown
- Élément 1
- Élément 2
  - Sous-élément
```

- **Liste numérotée** :
```markdown
1. Élément 1
2. Élément 2
```

### Liens
```markdown
[Texte du lien](https://example.com)
```

### Images
```markdown
![Texte alternatif](https://example.com/image.png)
```

### Citations
```markdown
> Ceci est une citation.
```

### Code
- **Inline** : Utilisez des backticks : `` `code` ``
- **Bloc de code** :
```markdown
```javascript
function add(a, b) {
  return a + b;
}
```
```

---

## Syntaxe avancée

### Tableaux
```markdown
| Colonne 1 | Colonne 2 | Colonne 3 |
|-----------|-----------|-----------|
| Valeur 1  | Valeur 2  | Valeur 3  |
```

### Liens automatiques
```markdown
<https://example.com>
```

### Notes de bas de page
```markdown
Voici une phrase avec une note de bas de page[^1].

[^1]: Ceci est la note de bas de page.
```

### Checklists
```markdown
- [x] Tâche terminée
- [ ] Tâche en cours
```

---

## Bonnes pratiques

1. **Organiser les titres** : Utilisez une hiérarchie claire pour structurer votre contenu.
2. **Limiter les blocs de code** : Utilisez des blocs de code uniquement lorsque nécessaire.
3. **Ajouter des liens utiles** : Fournissez des liens vers des ressources externes pour enrichir votre contenu.
4. **Utiliser des tableaux** : Présentez les données complexes sous forme de tableaux pour une meilleure lisibilité.

---

## Outils utiles

- **Visual Studio Code** : Extension Markdown Preview pour visualiser le rendu.
- **Typora** : Éditeur Markdown avec aperçu en temps réel.
- **Dillinger** : Éditeur Markdown en ligne.
- **Pandoc** : Convertisseur Markdown vers d'autres formats (PDF, HTML, etc.).

---

## Liens utiles

- [Documentation officielle Markdown](https://daringfireball.net/projects/markdown/)
- [Guide Markdown GitHub](https://guides.github.com/features/mastering-markdown/)
- [Exemples Markdown](https://www.markdownguide.org/)