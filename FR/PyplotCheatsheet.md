# Guide Matplotlib.pyplot : Exemples et Explications

Ce document contient des exemples pratiques d'utilisation de **Matplotlib.pyplot** en Python, avec des commentaires détaillés pour chaque ligne.

---

## 1. Import de Matplotlib.pyplot

```python
# Import de la bibliothèque pyplot et création de l'alias 'plt'
import matplotlib.pyplot as plt
print("Matplotlib.pyplot importé avec succès\n")
```

---

## 2. Tracer une courbe simple

```python
# Liste des valeurs pour l'axe X
x = [1, 2, 3, 4, 5]
# Liste des valeurs pour l'axe Y
y = [2, 4, 6, 8, 10]

# Trace la courbe reliant les points (x, y)
plt.plot(x, y)
# Ajoute un titre au graphique
plt.title("Courbe simple")
# Ajoute un label pour l'axe X
plt.xlabel("X")
# Ajoute un label pour l'axe Y
plt.ylabel("Y")
# Affiche le graphique
plt.show()
```

---

## 3. Tracer plusieurs courbes

```python
# Axe X commun
x = [0, 1, 2, 3, 4]
# Valeurs pour la première courbe (x²)
y1 = [0, 1, 4, 9, 16]
# Valeurs pour la deuxième courbe (x³)
y2 = [0, 1, 8, 27, 64]

# Trace la première courbe avec label
plt.plot(x, y1, label="x²")
# Trace la deuxième courbe en pointillé avec label
plt.plot(x, y2, label="x³", linestyle="--")
# Titre du graphique
plt.title("Plusieurs courbes")
# Label axe X
plt.xlabel("X")
# Label axe Y
plt.ylabel("Y")
# Affiche la légende pour différencier les courbes
plt.legend()
# Affiche le graphique
plt.show()
```

---

## 4. Tracé avec des points et couleurs

```python
# Axe X
x = [1, 2, 3, 4, 5]
# Axe Y
y = [5, 7, 2, 4, 9]

# Trace les points rouges ('r'=red, 'o'=cercle)
plt.plot(x, y, 'ro')
# Titre du graphique
plt.title("Points rouges")
# Label axe X
plt.xlabel("X")
# Label axe Y
plt.ylabel("Y")
# Affiche le graphique
plt.show()
```

---

## 5. Histogramme

```python
# Import de NumPy pour générer des données aléatoires
import numpy as np
# 1000 valeurs aléatoires suivant une loi normale
data = np.random.randn(1000)

# Crée l'histogramme avec 30 barres et couleur personnalisée
plt.hist(data, bins=30, color='skyblue', edgecolor='black')
# Titre du graphique
plt.title("Histogramme")
# Label axe X
plt.xlabel("Valeur")
# Label axe Y
plt.ylabel("Fréquence")
# Affiche le graphique
plt.show()
```

---

## 6. Diagramme en barres

```python
# Liste des catégories
categories = ['A', 'B', 'C', 'D']
# Valeurs associées aux catégories
valeurs = [5, 7, 3, 8]

# Crée un diagramme en barres
plt.bar(categories, valeurs, color='orange')
# Titre du graphique
plt.title("Diagramme en barres")
# Label axe X
plt.xlabel("Catégorie")
# Label axe Y
plt.ylabel("Valeur")
# Affiche le graphique
plt.show()
```

---

## 7. Diagramme circulaire (pie)

```python
# Étiquettes des parts du camembert
labels = ['Pomme', 'Banane', 'Cerise', 'Orange']
# Pourcentage de chaque part
sizes = [25, 35, 20, 20]

# Crée le diagramme circulaire avec pourcentages et rotation initiale
plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=90)
# Titre du graphique
plt.title("Diagramme circulaire")
# Affiche le graphique
plt.show()
```

---

## 8. Sous-graphiques (subplots)

```python
# Génère 100 points entre 0 et 2π
x = np.linspace(0, 2*np.pi, 100)
# Valeurs de sin(x)
y1 = np.sin(x)
# Valeurs de cos(x)
y2 = np.cos(x)

# Crée le premier subplot (2 lignes, 1 colonne, 1er graphique)
plt.subplot(2, 1, 1)
# Trace sin(x) en rouge
plt.plot(x, y1, 'r')
# Titre du premier graphique
plt.title("sin(x)")

# Crée le deuxième subplot
plt.subplot(2, 1, 2)
# Trace cos(x) en bleu
plt.plot(x, y2, 'b')
# Titre du deuxième graphique
plt.title("cos(x)")

# Ajuste automatiquement les espacements entre les subplots
plt.tight_layout()
# Affiche les deux graphiques
plt.show()
```

---

## 9. Tracé avec style et grille

```python
# Génère 100 points entre 0 et 10
x = np.linspace(0, 10, 100)
# Valeurs de sin(x)
y = np.sin(x)

# Trace la courbe avec couleur verte, ligne pointillée, points cercles et épaisseur 2
plt.plot(x, y, color='green', linewidth=2, linestyle='-.', marker='o', markersize=4)
# Titre du graphique
plt.title("Courbe stylisée avec grille")
# Label axe X
plt.xlabel("X")
# Label axe Y
plt.ylabel("Y")
# Active la grille
plt.grid(True)
# Affiche le graphique
plt.show()
```