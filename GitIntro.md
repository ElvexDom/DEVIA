# Introduction à Git

Un tutoriel pour maîtriser le versioning en entreprise

---

## Les concepts fondamentaux

Comprendre les éléments clés de Git pour maîtriser le contrôle de version.

### Repository

Un dépôt contient tout l'historique de votre projet, tous les fichiers et les modifications.

### Commit

Une sauvegarde avec un message descriptif. Chaque commit représente un état du projet.

### Branch

Une branche est une ligne de développement indépendante. Travaillez sans affecter le code principal.

### Remote

Un dépôt distant (GitHub, GitLab) où vous partagez votre code avec l'équipe.

---

## Pourquoi Git ?

### Contrôle de version

Indispensable en entreprise pour gérer les modifications du code.

### Collaboration simplifiée

Travaillez en équipe sans conflits de fichiers.

### Historique complet

Tracez chaque modification et revenez en arrière si nécessaire.

### Sécurité des données

Évitez les pertes de données avec des sauvegardes distribuées.

---

## Clone, Pull, Push

Les trois opérations essentielles pour synchroniser votre travail avec le serveur distant.

### Clone

Télécharger un projet entier du serveur vers votre ordinateur

```bash
git clone <url_du_projet>
```

### Pull

Récupérer les dernières modifications du serveur

```bash
git pull origin main
```

### Push

Envoyer vos modifications au serveur

```bash
git push origin main
```

---

## Configuration initiale

Avant de commencer, configurez votre identité Git. Ces informations apparaîtront dans chaque commit.

```bash
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@example.com"
```

Vérifiez votre configuration :

```bash
git config --global --list
```

---

## Le workflow de base - Partie 1

Commencez par cloner un projet et vérifier son état.

### Cloner le projet

```bash
git clone https://github.com/user/project.git
```

### Vérifier l'état

```bash
git status
```

Affiche les fichiers modifiés et non suivis

---

## Le workflow de base - Partie 2

Ajoutez vos modifications et créez un commit pour les sauvegarder.

### Ajouter les modifications

```bash
git add nom_fichier.py
git add .
```

### Créer un commit

```bash
git commit -m "Ajoute la fonction de prédiction"
```

---

## Le workflow de base - Partie 3

Synchronisez votre travail avec le serveur distant pour collaborer en équipe.

### Envoyer au serveur

```bash
git push origin main
```

### Récupérer les modifications

```bash
git pull origin main
```

---

## Commandes essentielles - Récapitulatif

|Commande|Description|Usage|
|---|---|---|
|git clone|Télécharger un projet|Démarrage|
|git status|Vérifier l'état des fichiers|Quotidien|
|git add|Ajouter des modifications|Avant commit|
|git commit|Créer une sauvegarde|Quotidien|
|git push|Envoyer au serveur|Partage|
|git pull|Récupérer les modifications|Synchronisation|
|git branch|Créer/lister des branches|Développement|
|git log|Voir l'historique|Analyse|

---

## Exercice pratique et ressources

### Scénario

Vous travaillez en binôme sur un projet de machine learning.  
L'un crée une branche pour les données, l'autre pour le modèle. Vous devez fusionner vos travaux sans conflits.

- Clonez le dépôt commun
    
- Créez chacun une branche distincte
    
- Commitez vos modifications
    
- Poussez vers le serveur
    
- Fusionnez les branches
    

### Ressources

- Documentation officielle : [git-scm.com](https://git-scm.com/)
    
- Learn Git Branching (interactif) : [learngitbranching.js.org](https://learngitbranching.js.org)