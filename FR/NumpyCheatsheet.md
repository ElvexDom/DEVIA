# Guide NumPy : Exemples et Explications

Ce document contient des exemples pratiques d'utilisation de **NumPy** en Python, avec des commentaires détaillés et un affichage après chaque bloc de code.

---

## 1. Import de NumPy

```python
# Import de la bibliothèque NumPy et création de l'alias 'np'
import numpy as np  
print("NumPy importé avec succès\n")
```

---

## 2. Création de tableaux

```python
# Tableau 1D (vecteur)
tab1D = np.array([1, 2, 3, 4, 5])
# Tableau 2D (matrice 2x3)
tab2D = np.array([[1, 2, 3], [4, 5, 6]])
# Tableau 2x3 rempli de 0
zeros = np.zeros((2, 3))
# Tableau 2x3 rempli de 1
ones = np.ones((2, 3))
# Tableau 2x3 avec valeurs aléatoires entre 0 et 1
alea = np.random.rand(2, 3)

# Affichage des tableaux
print("tab1D :", tab1D)
print("tab2D :\n", tab2D)
print("zeros :\n", zeros)
print("ones :\n", ones)
print("alea :\n", alea, "\n")
```

---

## 3. Séquences numériques

```python
# Crée une séquence de 0 à 10 (exclu) avec pas de 2
seq = np.arange(0, 10, 2)
# Crée 5 valeurs également espacées entre 0 et 1 (inclus)
lin = np.linspace(0, 1, 5)

print("seq :", seq)
print("lin :", lin, "\n")
```

---

## 4. Opérations sur les tableaux 1D

```python
# Somme des éléments
somme = np.sum(tab1D)
# Moyenne
moyenne = np.mean(tab1D)
# Valeur maximale
max_val = np.max(tab1D)
# Valeur minimale
min_val = np.min(tab1D)
# Multiplication par 2 (élément par élément)
double_tab = tab1D * 2
# Élévation au carré (élément par élément)
carre_tab = tab1D ** 2

print("Somme tab1D :", somme)
print("Moyenne tab1D :", moyenne)
print("Max tab1D :", max_val)
print("Min tab1D :", min_val)
print("Double tab1D :", double_tab)
print("Carré tab1D :", carre_tab, "\n")
```

---

## 5. Opérations sur les matrices 2D

```python
# Somme des colonnes
somme_col = np.sum(tab2D, axis=0)
# Somme des lignes
somme_ligne = np.sum(tab2D, axis=1)
# Transposition
transpose = tab2D.T

print("Somme par colonne tab2D :", somme_col)
print("Somme par ligne tab2D :", somme_ligne)
print("Transpose tab2D :\n", transpose, "\n")
```

---

## 6. Reshape (changement de forme)

```python
# Création d'un tableau 1D
tab = np.array([1, 2, 3, 4, 5, 6])
# Changement de forme : 1D -> 2x3
tab_2x3 = tab.reshape(2, 3)

print("tab 1D -> 2x3 reshape :\n", tab_2x3, "\n")
```

---

## 7. Empilement de tableaux

```python
# Création du premier tableau
a = np.array([1, 2, 3])
# Création du second tableau
b = np.array([4, 5, 6])
# Empilement horizontal : [1 2 3 4 5 6]
hstack = np.hstack((a, b))
# Empilement vertical : [[1 2 3], [4 5 6]]
vstack = np.vstack((a, b))

print("hstack :", hstack)
print("vstack :\n", vstack, "\n")
```

---

## 8. Indexation et filtrage

```python
# Création d'un tableau
tab = np.array([10, 20, 30, 40, 50])
# Sélection des indices 0, 2, 4
selection = tab[[0, 2, 4]]
# Filtrage des éléments > 25
filtre = tab[tab > 25]
# Indices des éléments > 25
indices = np.where(tab > 25)

print("Sélection indices [0,2,4] :", selection)
print("Éléments > 25 :", filtre)
print("Indices éléments > 25 :", indices, "\n")
```

---

## 9. Fonctions mathématiques

```python
# Création d'un tableau 1D
tab = np.array([1, 2, 3, 4, 5])
# Racine carrée
racine = np.sqrt(tab)
# Logarithme naturel
logarithme = np.log(tab)
# Exponentiel
exponentielle = np.exp(tab)
# Valeurs aléatoires arrondies à 2 décimales
arrondi = np.round(np.random.rand(3) * 10, 2)

print("Racine carrée :", racine)
print("Logarithme naturel :", logarithme)
print("Exponentielle :",
```