# Guide SQL : commandes essentielles

Ce guide présente les commandes SQL principales pour **créer, manipuler et interroger** des bases de données. Il inclut des exemples concrets et des bonnes pratiques.

---

## 1. Créer une base de données

```sql
CREATE DATABASE nom_de_la_base;
```

**Exemple :**

```sql
CREATE DATABASE ma_bibliotheque;
```

> 💡 Astuce : utilisez des noms explicites et sans espaces.

---

## 2. Supprimer une base de données

```sql
DROP DATABASE nom_de_la_base;
```

**Exemple :**

```sql
DROP DATABASE ma_bibliotheque;
```

> ⚠️ Attention : supprime définitivement la base et toutes ses tables.

---

## 3. Créer une table

```sql
CREATE TABLE nom_de_la_table (
    colonne1 TYPE_DE_DONNEE [CONTRAINTE],
    colonne2 TYPE_DE_DONNEE [CONTRAINTE],
    ...
);
```

**Exemple :**

```sql
CREATE TABLE livres (
    id INT PRIMARY KEY,
    titre VARCHAR(100) NOT NULL,
    auteur_id INT,
    annee_publication INT,
    FOREIGN KEY (auteur_id) REFERENCES auteurs(id)
);
```

> 💡 `PRIMARY KEY` identifie chaque ligne de manière unique.  
> 💡 `FOREIGN KEY` établit une relation entre tables.

---

### Types de données courants

|Type|Usage|
|---|---|
|`INT`|Entiers|
|`VARCHAR(n)`|Texte jusqu’à n caractères|
|`TEXT`|Texte long|
|`DATE`|Dates|
|`BOOLEAN`|Vrai / Faux|
|`DECIMAL(p,s)`|Nombres à virgule avec précision|

### Contraintes courantes

- `NOT NULL` : interdit les valeurs vides
    
- `UNIQUE` : garantit l’unicité
    
- `PRIMARY KEY` : identifiant unique
    
- `FOREIGN KEY` : clé étrangère
    

---

## 4. Supprimer une table

```sql
DROP TABLE nom_de_la_table;
```

**Exemple :**

```sql
DROP TABLE livres;
```

> ⚠️ Toutes les données seront perdues.

---

## 5. Insérer des données

```sql
INSERT INTO nom_de_la_table (colonne1, colonne2, ...)
VALUES (valeur1, valeur2, ...);
```

**Exemple :**

```sql
INSERT INTO livres (id, titre, auteur_id, annee_publication)
VALUES (1, 'Le Petit Prince', 1, 1943);
```

---

## 6. Lire des données avec SELECT

### SELECT de base

```sql
SELECT colonne1, colonne2
FROM nom_de_la_table;
```

**Exemple :**

```sql
SELECT titre, auteur_id
FROM livres;
```

- `*` pour toutes les colonnes :
    

```sql
SELECT * FROM livres;
```

### WHERE : filtrer les résultats

```sql
SELECT *
FROM livres
WHERE annee_publication > 2000;
```

- Combiner conditions :
    

```sql
SELECT *
FROM livres
WHERE auteur_id = 1 AND annee_publication > 2000;
```

### DISTINCT : valeurs uniques

```sql
SELECT DISTINCT auteur_id
FROM livres;
```

### ORDER BY : trier les résultats

```sql
SELECT titre, annee_publication
FROM livres
ORDER BY annee_publication ASC;
```

- Tri multiple :
    

```sql
SELECT titre, auteur_id
FROM livres
ORDER BY auteur_id ASC, titre DESC;
```

### LIMIT : limiter le nombre de résultats

```sql
SELECT *
FROM livres
LIMIT 5;
```

### BETWEEN ... AND : plage de valeurs

```sql
SELECT *
FROM livres
WHERE annee_publication BETWEEN 1990 AND 2000;
```

### LIKE : filtrage par motif

```sql
SELECT *
FROM livres
WHERE titre LIKE 'Le%';
```

- `%` = n'importe quelle suite de caractères
    
- `_` = un seul caractère
    

### IN : plusieurs valeurs possibles

```sql
SELECT *
FROM livres
WHERE auteur_id IN (1, 2);
```

### Fonctions utiles

|Fonction|Exemple|Description|
|---|---|---|
|`COUNT(*)`|`SELECT COUNT(*) FROM livres;`|Compter le nombre de lignes|
|`SUM(colonne)`|`SELECT SUM(prix) FROM ventes;`|Somme des valeurs|
|`AVG(colonne)`|`SELECT AVG(prix) FROM ventes;`|Moyenne|
|`MAX(colonne)`|`SELECT MAX(annee_publication) FROM livres;`|Valeur maximale|
|`MIN(colonne)`|`SELECT MIN(annee_publication) FROM livres;`|Valeur minimale|

### Combinaison avancée

```sql
SELECT DISTINCT auteur_id
FROM livres
WHERE annee_publication > 2000
ORDER BY auteur_id ASC
LIMIT 10;
```

---

## 7. Mettre à jour des données (UPDATE)

```sql
UPDATE nom_de_la_table
SET colonne1 = nouvelle_valeur
WHERE condition;
```

**Exemple :**

```sql
UPDATE livres
SET annee_publication = 1944
WHERE id = 1;
```

> ⚠️ Sans `WHERE`, toutes les lignes seront modifiées.

---

## 8. Supprimer des données (DELETE)

```sql
DELETE FROM nom_de_la_table
WHERE condition;
```

**Exemple :**

```sql
DELETE FROM livres
WHERE id = 1;
```

> ⚠️ Sans `WHERE`, toutes les lignes seront supprimées.

---

## 9. Modifier la structure d’une table

- Ajouter une colonne :
    

```sql
ALTER TABLE livres
ADD COLUMN genre VARCHAR(50);
```

- Supprimer toutes les lignes :
    

```sql
TRUNCATE TABLE livres;
```

---

## 10. Combiner plusieurs tables (JOIN)

```sql
-- INNER JOIN : seulement les correspondances
SELECT livres.titre, auteurs.nom
FROM livres
INNER JOIN auteurs ON livres.auteur_id = auteurs.id;

-- LEFT JOIN : tous les livres, même sans auteur
SELECT livres.titre, auteurs.nom
FROM livres
LEFT JOIN auteurs ON livres.auteur_id = auteurs.id;

-- RIGHT JOIN : tous les auteurs, même sans livre
SELECT livres.titre, auteurs.nom
FROM livres
RIGHT JOIN auteurs ON livres.auteur_id = auteurs.id;

-- SELF JOIN : joindre la table avec elle-même
SELECT e1.nom AS employe, e2.nom AS manager
FROM employes e1
LEFT JOIN employes e2 ON e1.manager_id = e2.id;
```

---

## 11. Bonnes pratiques

- Nommer tables et colonnes de manière cohérente
    
- Indenter et commenter les requêtes
    
- Tester les requêtes sur une base dédiée avant d’agir sur les données principales