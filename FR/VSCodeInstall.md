# Mini-guide installation projet Python + VS Code + Jupyter

## 1️⃣ Installer Python

1. Aller sur : [Python Downloads](https://www.python.org/downloads/)
    
2. Choisir la version souhaitée (recommandé : dernière version stable 3.x)
    
3. Pendant l’installation :
    
    - **Cocher “Add Python to PATH”**
        
    - **Cocher “Disable path length limit”** pour éviter les problèmes liés aux chemins trop longs sur Windows
        
4. Vérifier dans un terminal :
    

``` bash
python --version
```

## 2️⃣ Installer VS Code

- Télécharger depuis : [Visual Studio Code](https://code.visualstudio.com/)
    
- Installer normalement.
    

## 3️⃣ Extensions VS Code

### 🟢 Indispensables

| Extension               | Explication                                                                                                                                                                                                                                |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Python (Microsoft)**  | Support Python de base, IntelliSense, exécution de scripts, debug basique.  <br>💡 Installe automatiquement **Pylance**, **Python Debugger** et **Python Environment** pour autocomplétion, débogage avancé et gestion des environnements. |
| **Jupyter (Microsoft)** | Travailler avec les notebooks `.ipynb`.  <br>💡 Installe automatiquement **Jupyter Cell Tags**, **Jupyter Keymap**, **Jupyter Notebook Renderers** et **Jupyter Slide Show** pour balises, raccourcis, rendus avancés et diaporamas.       |

### 🟡 Fortement recommandées

| Extension               | Explication                                                             |
| ----------------------- | ----------------------------------------------------------------------- |
| **Markdown All in One** | Édition et prévisualisation Markdown, table des matières et raccourcis. |
| **GitLens**             | Visualisation de l’historique Git et suivi des changements.             |
| **Black Formatter**     | Formatage automatique du code selon PEP8.                               |
| **isort**               | Tri automatique des imports Python.                                     |

### 🔵 Optionnelles

| Extension                      | Explication                                                       |
| ------------------------------ | ----------------------------------------------------------------- |
| **Python Docstring Generator** | Génération automatique de docstrings pour fonctions et classes.   |
| **Jupyter PowerToys**          | Ajoute des fonctionnalités pratiques pour Jupyter dans VS Code.   |
| **Flake8**                     | Analyse statique pour détecter les erreurs et problèmes de style. |
| **Visual Studio IntelliCode**  | Suggestions intelligentes basées sur IA pour compléter le code.   |

> Pour un setup minimal, installe seulement les **extensions indispensables**, puis ajoute les fortement recommandées et optionnelles selon les besoins.

> ⚠️ Note : **JupyterHub** est une solution serveur multi-utilisateurs pour Jupyter et n’est pas nécessaire pour un usage local.

## 4️⃣ Créer un environnement virtuel (venv)

Dans le dossier de ton projet :

``` bash
python -m venv .venv
```

### Activer le venv

- **Windows (PowerShell)** :
    

``` bash
.venv\Scripts\Activate.ps1
```

> ⚠️ Si tu rencontres une erreur de type **"execution of scripts is disabled by your policy"**  
> Exécute la commande suivante dans PowerShell (sans être administrateur) :

``` powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

✅ Cela permettra à PowerShell d’autoriser l’exécution des scripts de ton venv.

- **macOS / Linux** :
    

``` bash
source .venv/bin/activate
```

Dans VS Code : **Ctrl+Shift+P → Python: Select Interpreter → choisir `.venv`**

## 5️⃣ Installer les packages Python essentiels

Avec le venv activé, commence par mettre à jour pip :

``` bash
python -m pip install --upgrade pip
```

Puis installe les packages essentiels :

``` bash
pip install jupyter pandas numpy matplotlib seaborn scikit-learn ipykernel
```

## 6️⃣ Installer le kernel (si nécessaire)

Toujours avec le venv activé :
Installe le kernel **uniquement** si ton `.venv` n’apparaît pas déjà comme kernel dans VS Code / Jupyter :

``` bash
python -m ipykernel install --user --name=.venv --display-name "Python 3.x (.venv)"
```

- `--name` : nom interne du kernel
    
- `--display-name` : nom affiché dans VS Code pour choisir le kernel
    
> 💡 Note : `ipykernel` est nécessaire pour que ton venv apparaisse comme kernel dans Jupyter.

## 7️⃣ Vérifier Jupyter Notebook

1. Crée un fichier `mon_notebook.ipynb`
    
2. Sélectionne le kernel **Python 3.x (.venv)** dans VS Code
    
3. Test rapide :
    

``` python
import sys
print(sys.executable)
print(sys.version)
```

> Le chemin doit pointer vers ton `.venv`.

## 8️⃣ Configurer Git et GitHub

### 🔹 Installer Git (si pas déjà fait)

- Télécharger Git : [Git Downloads](https://git-scm.com/downloads)
    
- Vérifier l'installation :
    
``` bash
git --version
```

### 🔹 Initialiser ton projet Git

Dans le dossier de ton projet :

``` bash
git init
```

### 🔹 Ajouter ton projet à GitHub

1. Crée un nouveau repository sur GitHub.
    
2. Copie l’URL HTTPS du repository.
    
3. Dans ton terminal, ajoute ton projet et pousse-le :
    

``` bash
git remote add origin https://github.com/tonUser/tonRepo.git
git add .
git commit -m "Initial commit"
git push -u origin main
```

---

Ton environnement Python, VS Code et Git est maintenant prêt pour le développement. Tu peux commencer à créer et exécuter tes notebooks, gérer tes environnements virtuels et versionner ton code sur GitHub.