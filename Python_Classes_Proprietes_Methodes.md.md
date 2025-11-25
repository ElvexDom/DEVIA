# Classes, propriétés et méthodes en Python

## 0. Exemple d'une fonction simple

Avant de parler des classes et des méthodes, voici comment définir et appeler une fonction simple :

```python
def dire_bonjour(nom):
    """Fonction qui affiche un message de bienvenue"""
    print(f"Bonjour, {nom} !")

# Appel de la fonction
dire_bonjour("Alice")
dire_bonjour("Bob")  # Chaque appel affiche un message différent selon l'argument
```

**Output :**

```
Bonjour, Alice !
Bonjour, Bob !
```

💡 Ceci montre la définition et l'appel d'une fonction simple avec paramètre. Cela sert de base avant d'introduire les méthodes dans les classes.

---

## 1. Introduction

En Python, il est courant de protéger les attributs d'une classe (en les préfixant avec `_` ou `__`) pour éviter qu'ils soient modifiés directement depuis l'extérieur. Pour accéder ou modifier ces attributs de manière sécurisée, on utilise les **propriétés** avec les décorateurs `@property` et `@{property}.setter`.

Ce document inclut également les notions essentielles sur les **types de méthodes courantes**, utiles au quotidien.

---

## 2. Différence entre `_attribut` et `__attribut`

|Syntaxe|Convention|Accès depuis l’extérieur|Note|
|---|---|---|---|
|`_attribut`|Protégé|Possible mais déconseillé|Simple convention, utilisé pour signaler que l’attribut est interne à la classe|
|`__attribut`|Privé|Difficile, via `_Classe__attribut`|Name mangling automatique, utilisé pour vraiment cacher un attribut et éviter les collisions de noms|

**Exemples :**

```python
class Exemple:
    def __init__(self):
        self._nom = "Alice"     # protégé
        self.__prenom = "Bob"   # privé

e = Exemple()
print(e._nom)           # fonctionne, mais déconseillé
# print(e.__prenom)     # AttributeError
print(e._Exemple__prenom) # fonctionne grâce au name mangling
```

**Output :**

```
Alice
Bob
```

💡 `_nom` montre une convention pour signaler un attribut interne, alors que `__prenom` est fortement protégé par Python via le name mangling.

---

## 3. Exemple de classe avec plusieurs propriétés

```python
class Personne:
    def __init__(self, nom, age, sexe, taille, poids):
        self._nom = nom
        self._age = age
        self._sexe = sexe
        self._taille = taille
        self._poids = poids

    @property
    def nom(self):
        return self._nom

    @nom.setter
    def nom(self, valeur):
        if not valeur:
            raise ValueError("Le nom ne peut pas être vide.")
        self._nom = valeur

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, valeur):
        if valeur < 0:
            raise ValueError("L'âge doit être positif.")
        self._age = valeur

    @property
    def sexe(self):
        return self._sexe

    @sexe.setter
    def sexe(self, valeur):
        if valeur not in ["Homme", "Femme", "Autre"]:
            raise ValueError("Le sexe doit être 'Homme', 'Femme' ou 'Autre'.")
        self._sexe = valeur

    @property
    def taille(self):
        return self._taille

    @taille.setter
    def taille(self, valeur):
        if valeur <= 0:
            raise ValueError("La taille doit être positive (en cm).")
        self._taille = valeur

    @property
    def poids(self):
        return self._poids

    @poids.setter
    def poids(self, valeur):
        if valeur <= 0:
            raise ValueError("Le poids doit être positif (en kg).")
        self._poids = valeur

alice = Personne("Alice", 30, "Femme", 165, 60)
bob = Personne("Bob", 35, "Homme", 180, 75)

print(f"{alice.nom} {alice.age}ans {alice.sexe} {alice.taille}cm {alice.poids}kg")
print(f"{bob.nom} {bob.age}ans {bob.sexe} {bob.taille}cm {bob.poids}kg")
```

**Output :**

```
Alice 30ans Femme 165cm 60kg
Bob 35ans Homme 180cm 75kg
```

💡 Chaque propriété permet d’accéder ou modifier un attribut avec validation, montrant l’encapsulation et la sécurité des données.

---

## 4. Explication des décorateurs

### 4.1 `@property`

- Transforme une méthode en **attribut en lecture seule**.
    
- Permet d'accéder à un attribut protégé comme si c'était un attribut normal.
    

### 4.2 `@{property}.setter`

- Définit un setter pour la propriété existante.
    
- Permet de valider ou modifier la valeur avant de la stocker.
    

💡 Les décorateurs simplifient la syntaxe et protègent les données tout en conservant un accès naturel via `obj.attribut`.

---

## 5. Types de méthodes courantes en Python

|Type de méthode|Décorateur|Paramètre principal|Utilité|
|---|---|---|---|
|Méthode d'instance|_(aucun)_|`self`|Manipuler les attributs d'un objet|
|Méthode de classe|`@classmethod`|`cls`|Créer des objets différemment, constructeurs alternatifs|
|Méthode statique|`@staticmethod`|Aucun|Fonction utilitaire regroupée dans la classe|
|Propriété (getter)|`@property`|`self`|Accès contrôlé à un attribut|
|Propriété (setter)|`@{property}.setter`|`self`|Validation de données à l'écriture|
|Propriété (deleter)|`@{property}.deleter`|`self`|Suppression contrôlée d’un attribut|
|Méthode protégée|`_methode`|`self`|Usage interne, convention|
|Méthode privée|`__methode`|`self`|Protection forte, name mangling|

### 5.1 Méthodes publiques d’instance

```python
class Personne:
    def __init__(self, nom):
        self.nom = nom

    def dire_bonjour(self):
        print(f"Bonjour, je m'appelle {self.nom} !")

p = Personne("Alice")
p.dire_bonjour()  # publique
```

**Output :**

```
Bonjour, je m'appelle Alice !
```

💡 Montre comment une méthode classique agit sur une instance et peut accéder aux attributs via `self`.

### 5.2 Méthodes protégées d’instance

```python
class Personne:
    def _interne(self):
        print("Méthode protégée")

p = Personne()
p._interne()  # accessible mais usage interne conseillé
```

💡 Le préfixe `_` indique une méthode à usage interne, c’est une convention pour signaler aux développeurs de ne pas l’utiliser directement.

### 5.3 Méthodes privées d’instance

```python
class Personne:
    def __secret(self):
        print("Méthode privée")

p = Personne()
p._Personne__secret()  # accessible via name mangling
```

💡 Double underscore `__` protège fortement la méthode, rendant son accès difficile depuis l’extérieur.

### 5.4 Méthodes de classe

```python
class Personne:
    def __init__(self, nom):
        self._nom = nom
    @classmethod
    def creer_anonyme(cls):
        return cls("Inconnu")

p = Personne.creer_anonyme()
print(p.nom)  # Inconnu
```

💡 `cls` permet de se référer à la classe et de créer une instance depuis la méthode, utile pour des constructeurs alternatifs.

### 5.5 Méthodes statiques

```python
class Maths:
    @staticmethod
    def addition(a, b):
        return a + b

print(Maths.addition(3, 5))  # 8
```

💡 Pas besoin de `self` ou `cls`, la méthode est indépendante et sert de fonction utilitaire.

### 5.6 Propriétés (getter, setter, deleter)

```python
class Personne:
    def __init__(self, age):
        self._age = age

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, valeur):
        if valeur < 0:
            raise ValueError("L'âge doit être positif")
        self._age = valeur

    @age.deleter
    def age(self):
        print("Suppression de l'âge")
        del self._age
```

💡 Les propriétés permettent un accès simple et naturel aux attributs tout en appliquant une validation.

---

## 6. Méthodes magiques utiles

|Méthode|Utilité|
|---|---|
|`__init__`|Constructeur, appelé lors de la création d'une instance|
|`__str__`|Affichage lisible avec `print(obj)`|
|`__repr__`|Représentation officielle, utile pour le debug|
|`__len__`|Compatibilité avec `len(obj)`|
|`__eq__`|Comparaison `==` entre objets|
|`__add__`|Surcharge de l'opérateur `+`|
|`__getitem__`|Accès indexé `obj[i]` pour les objets séquentiels|

### Exemple

```python
class Nombre:
    def __init__(self, n):
        self.n = n

    def __add__(self, autre):
        return self.n + autre.n

    def __str__(self):
        return str(self.n)

a = Nombre(5)
b = Nombre(7)
print(a + b)  # 12
print(a)       # 5
```

💡 Les méthodes magiques permettent de redéfinir le comportement de base des objets (affichage, opérateurs, etc.) pour une utilisation plus naturelle.

---

## 7. Modules et Packages

### Modules

Un module est un fichier Python `.py` contenant fonctions, classes et variables pour organiser le code.

### Packages

Un **package** est un répertoire contenant plusieurs modules et un fichier `__init__.py`. Il permet de structurer le code.

### Imports selon la structure des dossiers

#### Script et package dans le même dossier

```
projet/
├── main.py
└── mon_package/
    ├── __init__.py
    ├── module_a.py
    └── module_b.py
```

```python
from mon_package import module_a
```

#### Package dans un sous-dossier

```
projet/
├── main.py
└── src/
    └── mon_package/
        ├── __init__.py
        ├── module_a.py
        └── module_b.py
```

**Solution 1 : ajouter le chemin au sys.path**

```python
import sys
sys.path.append("src")
from mon_package import module_a
```

**Solution 2 : lancer le script depuis le dossier src**

```bash
cd src
python ../main.py
```

#### Exécuter un module directement avec -m

```bash
python -m src.mon_package.module_a
```

#### Imports relatifs dans les modules

```python
# module_b.py
from .module_a import fonction_a  # le point signifie "même package"
```

💡 **Bonnes pratiques :**

- Toujours avoir un `__init__.py` dans chaque dossier de package
    
- Privilégier les imports relatifs pour les modules internes
    
- Structurer le projet avec un dossier `src/` pour les packages et `tests/` pour les tests
    

### Importer une classe entière depuis un module ou package

#### Si `__init__.py` est vide

```python
from mon_package.personne import Personne
alice = Personne("Alice")
alice.dire_bonjour()

import mon_package.personne
bob = mon_package.personne.Personne("Bob")
bob.dire_bonjour()
```

💡 Tu dois préciser le module (`personne`) pour accéder à la classe.

#### Si `__init__.py` expose la classe

```python
# mon_package/__init__.py
from .personne import Personne
```

```python
from mon_package import Personne
alice = Personne("Alice")
alice.dire_bonjour()
```

💡 Dans ce cas, tu peux importer la classe directement depuis le package sans préfixer le module.