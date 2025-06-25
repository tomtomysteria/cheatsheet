# 📦 Python

## Introduction

Python est un langage de programmation interprété, polyvalent et facile à apprendre. Il est largement utilisé pour le développement web, l'analyse de données, l'intelligence artificielle, et l'automatisation. Grâce à sa vaste bibliothèque standard et ses frameworks comme Django et Flask, Python simplifie le développement d'applications robustes et scalables.

---

## Commandes essentielles

### Python CLI

```bash
python --version                      # Affiche la version de Python
python <file>.py                      # Exécute un fichier Python
pip install <package>                 # Installe un package via pip
pip uninstall <package>               # Supprime un package
pip list                              # Liste les packages installés
pip freeze > requirements.txt         # Génère un fichier des dépendances
pip install -r requirements.txt       # Installe les dépendances depuis un fichier
python -m venv <env-name>             # Crée un environnement virtuel
source <env-name>/bin/activate        # Active l'environnement virtuel (Linux/Mac)
<env-name>\Scripts\activate           # Active l'environnement virtuel (Windows)
deactivate                            # Désactive l'environnement virtuel
pytest                                # Exécute les tests avec pytest
```

---

## Concepts clés

### Lecture et écriture dans un fichier

#### Écriture dans un fichier

```python
# filepath: utils/file_utils.py
def write_to_file(filename, content):
    with open(filename, 'w') as file:
        file.write(content)
```

#### Lecture d'un fichier

```python
# filepath: utils/file_utils.py
def read_from_file(filename):
    with open(filename, 'r') as file:
        return file.read()
```

---

## Analyse de données avec NumPy et Pandas

### Installation

Ajoutez NumPy et Pandas au projet :

```bash
pip install numpy pandas
```

### Exemple avec NumPy

```python
# filepath: utils/numpy_example.py
import numpy as np

def calculate_mean(numbers):
    array = np.array(numbers)
    return np.mean(array)
```

### Exemple avec Pandas

```python
# filepath: utils/pandas_example.py
import pandas as pd

def create_dataframe(data):
    return pd.DataFrame(data)

def filter_dataframe(df, column, value):
    return df[df[column] == value]
```

---

## Développement web avec Flask

### Exemple de route

```python
# filepath: app.py
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/api/hello', methods=['GET'])
def hello():
    return jsonify({"message": "Hello, Flask!"})

if __name__ == '__main__':
    app.run(debug=True)
```

---

## ORM avec SQLAlchemy

### Exemple d'entité

```python
# filepath: models/user.py
from sqlalchemy import Column, Integer, String
from sqlalchemy.ext.declarative import declarative_base

Base = declarative_base()

class User(Base):
    __tablename__ = 'users'

    id = Column(Integer, primary_key=True, autoincrement=True)
    name = Column(String, nullable=False)
    email = Column(String, unique=True, nullable=False)
```

### Configuration de SQLAlchemy

```python
# filepath: config/database.py
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker

DATABASE_URL = "sqlite:///./test.db"

engine = create_engine(DATABASE_URL)
SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)
```

---

## Services

### Exemple de service

```python
# filepath: services/user_service.py
from models.user import User
from config.database import SessionLocal

class UserService:
    def get_user_by_email(self, email):
        session = SessionLocal()
        user = session.query(User).filter(User.email == email).first()
        session.close()
        return user
```

---

## Tests avec pytest

### Installation de pytest

Ajoutez pytest au projet :

```bash
pip install pytest
```

#### Exemple de test

```python
# filepath: tests/test_math_utils.py
from utils.math_utils import add, subtract

def test_add():
    assert add(2, 3) == 5

def test_subtract():
    assert subtract(5, 3) == 2
```

Exécutez les tests :

```bash
pytest
```

---

## Gestion des logs

### Utilisation de `logging`

```python
# filepath: utils/logger.py
import logging

logging.basicConfig(level=logging.DEBUG, format='%(asctime)s - %(levelname)s - %(message)s')

def log_info(message):
    logging.info(message)

def log_warning(message):
    logging.warning(message)

def log_error(message):
    logging.error(message)
```

---

## Bonnes pratiques

1. **Structurer les projets** : Organisez les fichiers en dossiers (ex. `models`, `services`, `utils`, `tests`) pour améliorer la maintenabilité.
2. **Utiliser les environnements virtuels** : Gérez les dépendances avec des environnements virtuels.
3. **Automatiser les tests** : Intégrez les tests dans les pipelines CI/CD pour garantir la qualité du code.
4. **Activer les logs** : Configurez `logging` pour surveiller les performances et les erreurs.
5. **Utiliser des fichiers de configuration** : Gérez les paramètres avec des fichiers `.env` ou `config.py`.
6. **Optimiser les performances** : Utilisez des outils de profiling pour identifier les goulots d'étranglement.
7. **Utiliser des services** : Centralisez la logique métier dans des services pour améliorer la maintenabilité.
8. **Utiliser SQLAlchemy** : Simplifiez la gestion des bases de données avec SQLAlchemy.
9. **Utiliser NumPy et Pandas** : Simplifiez l'analyse et la manipulation des données avec ces bibliothèques.

---

## Liens utiles

- [Documentation officielle Python](https://docs.python.org/3/)
- [Documentation Flask](https://flask.palletsprojects.com/)
- [Documentation SQLAlchemy](https://docs.sqlalchemy.org/)
- [Documentation NumPy](https://numpy.org/doc/)
- [Documentation Pandas](https://pandas.pydata.org/docs/)
- [Tutoriels Python](https://www.w3schools.com/python/)
- [Exemples de projets Python](https://github.com/python/cpython)
- [Documentation pytest](https://docs.pytest.org/)
