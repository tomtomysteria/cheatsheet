# 📦 Python

## Introduction

Python est un langage de programmation interprété, polyvalent et facile à apprendre. Il est largement utilisé pour le développement web, l'analyse de données, l'intelligence artificielle, et l'automatisation.

---

## Commandes essentielles

### Gestion des fichiers Python

```bash
python --version                     # Affiche la version de Python installée
python script.py                     # Exécute un fichier Python
python -m venv env                   # Crée un environnement virtuel
source env/bin/activate              # Active un environnement virtuel (Linux/Mac)
env\Scripts\activate                 # Active un environnement virtuel (Windows)
deactivate                           # Désactive l'environnement virtuel
```

### Gestion des packages avec pip

```bash
pip install <package>                # Installe un package
pip uninstall <package>              # Désinstalle un package
pip list                             # Liste les packages installés
pip freeze > requirements.txt        # Génère un fichier des dépendances
pip install -r requirements.txt      # Installe les dépendances depuis un fichier
```

---

## Exemples pratiques

### Exemple de script Python simple

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("World"))
```

### Lecture et écriture de fichiers

```python
# Écriture dans un fichier
with open("example.txt", "w") as file:
    file.write("Hello, File System!")

# Lecture d'un fichier
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

### Utilisation des bibliothèques populaires

#### NumPy pour les calculs scientifiques

```python
import numpy as np

array = np.array([1, 2, 3, 4])
print(array.mean())
```

#### Pandas pour l'analyse de données

```python
import pandas as pd

data = {"Name": ["Alice", "Bob"], "Age": [25, 30]}
df = pd.DataFrame(data)
print(df)
```

#### Flask pour le développement web

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello, Flask!"

if __name__ == "__main__":
    app.run(debug=True)
```

---

## Bonnes pratiques

1. **Utiliser des environnements virtuels** : Isolez les dépendances de chaque projet avec `venv`.
2. **Respecter les conventions PEP 8** : Suivez les conventions de style pour écrire du code Python lisible et maintenable.
3. **Documenter le code** : Ajoutez des docstrings pour expliquer les fonctions et classes.

---

## Liens utiles

- [Documentation officielle Python](https://www.python.org/doc/)
- [Tutoriels Python](https://www.w3schools.com/python/)
- [Exemples de projets Python](https://github.com/TheAlgorithms/Python)
