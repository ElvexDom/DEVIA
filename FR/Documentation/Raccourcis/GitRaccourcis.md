---
tags:
  - "#VSCode"
  - "#Git"
  - "#Commandes"
---
# Commandes Git

Liste complète des commandes Git essentielles pour gérer tes projets.

---

## 1. Configuration

- `git config --global user.name "Nom"` → définir ton nom d’utilisateur  
- `git config --global user.email "email@example.com"` → définir ton email  
- `git config --list` → vérifier la configuration  

---

## 2. Initialisation et clonage

- `git init` → créer un dépôt Git local  
- `git clone <url>` → cloner un dépôt distant  

---

## 3. Gestion des fichiers

- `git status` → voir l’état des fichiers  
- `git add <fichier>` → ajouter un fichier à l’index  
- `git add .` → ajouter tous les fichiers modifiés  
- `git rm <fichier>` → supprimer un fichier du dépôt  

---

## 4. Commit

- `git commit -m "Message"` → enregistrer les modifications  
- `git commit -a -m "Message"` → ajouter et committer en une seule commande  

---

## 5. Branches

- `git branch` → lister les branches locales  
- `git branch <nom>` → créer une nouvelle branche  
- `git checkout <nom>` → basculer sur une branche  
- `git checkout -b <nom>` → créer et basculer sur une nouvelle branche  
- `git merge <branche>` → fusionner une branche dans la branche courante  
- `git branch -d <nom>` → supprimer une branche locale  

---

## 6. Historique et logs

- `git log` → voir l’historique des commits  
- `git log --oneline` → historique simplifié  
- `git log --graph --oneline --all` → graphique de toutes les branches  

---

## 7. Dépôt distant (GitHub, GitLab…)

- `git remote -v` → afficher les dépôts distants  
- `git remote add origin <url>` → ajouter un dépôt distant  
- `git push -u origin <branche>` → envoyer une branche locale sur le dépôt distant  
- `git pull` → récupérer les modifications du dépôt distant  

---

## 8. Revert et reset

- `git reset --hard <commit>` → revenir à un commit précédent  
- `git revert <commit>` → créer un commit annulant un commit précédent  
- `git checkout -- <fichier>` → annuler les modifications locales sur un fichier  

---

## 9. Stash (mettre de côté temporairement)

- `git stash` → mettre les modifications de côté  
- `git stash list` → lister les stashes  
- `git stash apply` → récupérer le dernier stash  
- `git stash pop` → récupérer et supprimer le dernier stash  

---

## 10. Différences et comparaison

- `git diff` → voir les différences non indexées  
- `git diff --staged` → voir les différences indexées  
- `git show <commit>` → voir les changements dans un commit spécifique  

---
[⬅ Retour](../Documentation.md)