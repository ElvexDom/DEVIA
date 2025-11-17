---

tags:

- "#Python"
    
- "#Installation"
    
- "#Environnement"
    

---

# Python – Installation et Environnement

Guide complet pour installer Python, configurer l’environnement et gérer les dépendances.

---

## 1. Installation de Python

- Télécharger Python : [python.org](https://www.python.org/downloads/)

- Vérifier l’installation :


```bash
python --version
```

- Sur Windows, cocher “Add Python to PATH” lors de l’installation.

## 2. Gestion des environnements virtuels

Créer un environnement virtuel :

```bash
python -m venv .venv
```

Activer l’environnement :

**Windows :**

```bash
.venv\Scripts\activate
```

**Mac/Linux :**

```bash
source .env/bin/activate
```

Désactiver l’environnement :

```bash
deactivate
```

## 3. Gestion des paquets

Installer un paquet :

```bash
pip install <package>
```

Mettre à jour pip :

```bash
python -m pip install --upgrade pip
```

Lister les paquets installés :

```bash
pip list
```

Générer un fichier des dépendances :

```bash
pip freeze > requirements.txt
```

Installer depuis un fichier requirements :

```bash
pip install -r requirements.txt
```

## 4. Conseils pratiques

- Créer un environnement virtuel par projet pour éviter les conflits de dépendances.

- Vérifier la version de Python et des packages avant de commencer un projet.


## 5. Liens utiles

- [Documentation Python venv](https://docs.python.org/3/library/venv.html)

- [Pip Documentation](https://pip.pypa.io/en/stable/)

- [Conda Environment Guide](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)


---
