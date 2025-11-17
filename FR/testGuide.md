# Guide complet des tests en Python

Ce guide présente les bonnes pratiques pour mettre en place des tests unitaires, d’intégration, fonctionnels et de performance dans un projet Python, en utilisant les frameworks **Doctest**, **Pytest** et **Unittest**.
Il suit un parcours progressif depuis la découverte des tests jusqu’à l’implémentation dans un projet concret.

---

## 1. Introduction aux tests

### Pourquoi tester ?

* Les tests permettent de **réduire le risque de bugs** dans votre code.
* Chaque test vérifie qu’une partie du programme fonctionne correctement.
* Ils assurent qu’une nouvelle fonctionnalité n’impacte pas le fonctionnement existant.
* Les tests automatisés économisent du temps et facilitent la collaboration.

### Tests manuels vs automatisés

* **Tests automatisés** : écrits par des développeurs, exécutés par l’ordinateur. Vérifient les spécifications techniques.
* **Tests manuels** : réalisés par un humain (responsable qualité ou client). Vérifient les spécifications fonctionnelles.

---

## 2. La pyramide des tests

1. **Tests unitaires** (base) :

   * Testent une unité de code (fonction ou méthode).
   * Ne dépendent pas de ressources externes (base de données, API).
   * Exemple : vérifier que `nourrir_crocodile()` met à jour la date du dernier repas.

2. **Tests d’intégration** :

   * Vérifient que plusieurs fonctionnalités fonctionnent ensemble.
   * Exemple : `servir_repas()` utilise `nourrir_crocodile()` pour tous les crocodiles.

3. **Tests fonctionnels** :

   * Vérifient que le parcours utilisateur fonctionne correctement.
   * Automatisés avec des librairies comme Selenium.
   * Exemple : ajouter un crocodile via l’interface et vérifier la confirmation.

4. **Tests de performance** :

   * Évaluent la vitesse et la stabilité sous charge.
   * Exemple : simuler des requêtes sur l’application pour mesurer le temps de réponse.

5. **Tests d’acceptation** :

   * Réalisés par le client pour valider que la fonctionnalité correspond aux attentes.
   * Exemple : le client ajoute un crocodile et valide le processus.

---

## 3. Décelez les éléments à tester

### Identifier quoi tester

* **Tester l’interface publique des objets**, pas les méthodes privées.
* **Tests unitaires sur chaque méthode publique** : chaque scénario possible de sortie doit être testé.
* Éviter de tester le détail de l’implémentation, car les modifications peuvent casser les tests existants.

### Plan de test

Pour chaque cas de test :

* Type de test (unitaire, intégration, fonctionnel…)
* Unité de code à tester
* Entrées (`inputs`)
* Sorties attendues (`outputs`)

### Exemple : classe `Calculator`

```python
import re

class Calculator:
    def __init__(self):
        self.left_value = 0
        self.right_value = 0

    def calculate(self, operation):
        if self._check_and_set_value(operation):
            if "+" in operation:
                return self.left_value + self.right_value
            elif "-" in operation:
                return self.left_value - self.right_value
            elif "*" in operation:
                return self.left_value * self.right_value
            elif "/" in operation:
                try:
                    return self.left_value / self.right_value
                except ZeroDivisionError:
                    return "Invalid operation : Zero Division Error"
            else:
                return "Invalid operation"
        else:
            return "Invalid operation"

    def _check_and_set_value(self, operation):
        operation = operation.replace(" ", "")
        values = re.split('\+|\-|\*|\/', operation)
        if len(values) == 2:
            try:
                self.left_value = float(values[0])
                self.right_value = float(values[1])
                return True
            except ValueError:
                return False
        else:
            return False
```

Stratégie : tester toutes les sorties possibles de la méthode `calculate()`.

---

## 4. Tests avec Doctest

### Exemple : fonction `to_absolute`

```python
def to_absolute(number):
    """
    Return the absolute value

    >>> to_absolute(3)
    3
    >>> to_absolute(-10)
    10
    """
    if number <= 0:
        return -number
    return number
```

### Exécution

```bash
python -m doctest main.py
python -m doctest -v main.py
```

Les doctests servent à **documenter et tester** le comportement d’une fonction.

Pour un projet complet, il est préférable de créer un **fichier dédié aux tests**.

---

## 5. Tests avec Pytest

### Installation

```bash
pip install -U pytest
```

### Exemple de test Pytest

Fonction à tester :

```python
# source.py
def reverse_str(initial_string):
    final_string = ''
    index = len(initial_string)
    while index > 0:
        final_string += initial_string[index - 1]
        index -= 1
    return final_string
```

Fichier de test :

```python
# test.py
from source import reverse_str

def test_should_reverse_string():
    assert reverse_str('abc') == 'cba'
```

### Exécution

```bash
pytest test.py
```

### Bonnes pratiques Pytest

* Créer un répertoire `tests/` séparé du code source.
* Nommer les fichiers `test_<nom_du_module>.py` ou `<nom_du_module>_test.py`.
* Chaque fonction de test doit commencer par `test_`.
* Utiliser `assert` pour valider le résultat attendu.

Exemple projet Calculatrice :

```python
# tests/test_operators.py
from calculate.operators import Operators

def test_should_make_multiple_addition():
    sut = Operators()
    operation = "5.5 + 10 + 30 + 13.7"
    expected_value = 59.2
    assert sut.addition(operation) == expected_value
```

---

## 6. Tests avec Unittest

### Structure

* Créer une classe héritant de `unittest.TestCase`.
* Les scénarios sont des méthodes de la classe.
* Ajouter `unittest.main()` à la fin du fichier.

### Méthodes d’assertion

| Méthode                | Vérifie que      |
| ---------------------- | ---------------- |
| assertEqual(a, b)      | a == b           |
| assertNotEqual(a, b)   | a != b           |
| assertTrue(a)          | bool(a) is True  |
| assertFalse(a)         | bool(a) is False |
| assertIs(a, b)         | a is b           |
| assertIsNot(a, b)      | a is not b       |
| assertIsNone(a)        | a is None        |
| assertIsNotNone(a)     | a is not None    |
| assertIn(a, b)         | a in b           |
| assertNotIn(a, b)      | a not in b       |
| assertIsInstance(a, b) | isinstance(a, b) |

### Exemple

```python
import unittest

class TestString(unittest.TestCase):

    def test_should_capitalize_string(self):
        string = "hello"
        expected_value = "Hello"
        self.assertEqual(string.capitalize(), expected_value)

    def test_should_upper_string(self):
        string = "hello"
        expected_value = "HELLO"
        self.assertEqual(string.upper(), expected_value)

    def test_should_trim_string(self):
        string = "  hello "
        expected_value = "hello"
        self.assertEqual(string.strip(), expected_value)

if __name__ == "__main__":
    unittest.main()
```

### Exécution

```bash
python -m unittest test_string
```

### Bonnes pratiques

* Organiser les tests dans un répertoire séparé.
* Nommer les méthodes de test avec le préfixe `test_`.
* Ajouter `unittest.main()` à la fin du fichier.
* Tester les modules view et operators avant d’aborder les mocks pour controller.

---

## 7. Conclusion

* Commencez par identifier les éléments à tester et créez un plan de tests.
* Testez l’interface publique des objets, pas leurs méthodes internes.
* Les frameworks Python principaux : Doctest, Pytest, Unittest.
* Organisez vos tests dans un répertoire dédié, calqué sur l’arborescence du code source.
* Utilisez les assertions pour valider vos tests.
* Lancez régulièrement les tests pour prévenir les régressions et sécuriser vos développem
