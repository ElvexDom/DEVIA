---
tags:
  - "#FR"
  - "#Python"
  - "#Jupyter"
  - "#Exercices"
type: Exercices
---

# EXERCICES NUMPY

Ce fichier contient 10 exercices pratiques pour s'entraîner avec **NumPy**.  
Chaque exercice est suivi d'un exemple de solution.

---

## 1 - Créez un tableau NumPy contenant les entiers de 1 à 10 (inclus)

```python
import numpy as np

tableau_entiers = np.arange(1, 11)
tableau_entiers
```

---

## 2 - Créez un tableau NumPy contenant 5 valeurs flottantes générées aléatoirement entre 0 et 1

```python
tableau_flottants = np.random.rand(5)
tableau_flottants
```

---

## 3 - Créez une fonction qui prend un tableau NumPy en entrée et renvoie la somme de ses éléments

```python
def somme_tableau(tableau):
    return np.sum(tableau)

print("Somme tableau entiers :", int(somme_tableau(tableau_entiers)))
print("Somme tableau flottants :", float(somme_tableau(tableau_flottants)))
```

---

## 4 - Créez une fonction qui prend deux tableaux NumPy et renvoie le produit scalaire (dot product)

```python
def produit_scalaire(t1, t2):
    return np.dot(t1, t2)

print("Produit scalaire tableau entiers :", produit_scalaire(tableau_entiers, tableau_entiers))
print("Produit scalaire tableau flottants :", produit_scalaire(tableau_flottants, tableau_flottants))
```

---

## 5 - Créez une fonction qui renvoie un nouveau tableau contenant uniquement les éléments uniques

```python
def elements_uniques(tableau):
    return np.unique(tableau)

tableau = np.array([2, 4, 2, 3, 4, 4, 6])
print("Éléments uniques :", elements_uniques(tableau))
```

---

## 6 - Créez une fonction qui renvoie un tableau trié par ordre croissant

```python
def trier_tableau(tableau):
    return np.sort(tableau)

tableau = np.array([8, 4, 8, 6, 9])
print("Éléments triés :", trier_tableau(tableau))
```

---

## 7 - Créez une fonction qui renvoie la moyenne, la médiane et l'écart type

```python
def statistiques_tableau(tableau):
    moyenne = np.mean(tableau)
    mediane = np.median(tableau)
    ecart_type = np.std(tableau)
    return moyenne, mediane, ecart_type

stats_entiers = statistiques_tableau(tableau_entiers)
stats_flottants = statistiques_tableau(tableau_flottants)

print(f"Tableau entiers : Moyenne={stats_entiers[0]}, Médiane={stats_entiers[1]}, Écart type={stats_entiers[2]}")
print(f"Tableau flottants : Moyenne={stats_flottants[0]}, Médiane={stats_flottants[1]}, Écart type={stats_flottants[2]}")
```

---

## 8 - Créez une fonction qui transforme un tableau (0 si <5, 1 si >=5)

```python
def transformer_tableau(tableau):
    return np.where(tableau < 5, 0, 1)

tableau = np.array([5, 8, 2, 3, 10])
tableau_transform = transformer_tableau(tableau)
print("Éléments transformés :", tableau_transform)
```

---

## 9 - Créez une fonction qui renvoie un tableau contenant uniquement les nombres premiers

```python
def nombre_premier(n):
    if n <= 1:
        return False
    for i in range(2, n):
        if n % i == 0:
            return False
    return True

tableau_premier = np.array([x for x in tableau_entiers if nombre_premier(x)])
print("Tableau des nombres premiers :", tableau_premier)
```

---

## 10 - Créez un tableau NumPy 2D 3x3 avec valeurs entières aléatoires entre 1 et 10

```python
tableau_2d = np.random.randint(1, 11, size=(3, 3))
print("
```


---
