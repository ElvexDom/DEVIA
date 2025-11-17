---
tags:
  - "#FR"
  - "#VSCode"
  - "#Astuces"
  - "#Snippets"
category: "Documentation"
tool: "VSCode"
---

# Snippets VS Code

Ressources et conseils détaillés pour créer et utiliser des snippets dans VS Code afin de gagner du temps et améliorer votre productivité.

---

> **Astuce :** pour insérer un snippet, tapez le **préfixe** puis appuyez sur `Ctrl+Space`.

[🇬🇧 Switch to English](../../EN/Documentation/Tips/VSCodeSnippets_EN.md)

---

## 1️⃣ Créer un snippet global

1. Ouvrir la palette de commandes : `Ctrl+Shift+P`  
2. Taper `Configure User Snippets` → `New Global Snippet File`  
3. Donner un nom au fichier (ex : `mes_snippets.code-snippets`)  
4. Ajouter vos snippets au format JSON.

---

## 2️⃣ Exemple de snippet simple

Taper **hello** puis `Ctrl+Space` pour insérer :

```json
{
  "Print Hello": {
    "prefix": "hello",
    "body": [
      "def hello_world():",
      "    print('Hello World')"
    ],
    "description": "Snippet pour afficher Hello World"
  }
}
```

**Comment ça marche :**

- `prefix` : mot que tu tapes (hello)  
- `body` : le code inséré  
- `description` : ce que fait le snippet  

---

## 3️⃣ Exemple avec placeholders

```json
{
  "Function Template": {
    "prefix": "func",
    "body": [
      "def ${1:function_name}(${2:args}):",
      "    """${3:description}"""",
      "    ${0:pass}"
    ],
    "description": "Modèle de fonction Python avec placeholders"
  }
}
```

**Explications :**

- `${1:...}` : premier champ à compléter, puis Tab pour passer au suivant  
- `${0}` : position finale du curseur après remplissage  

---

## 4️⃣ Snippets avec variables intégrées

```json
{
  "Print File Name": {
    "prefix": "pfname",
    "body": [
      "print(\"Fichier : ${TM_FILENAME}\")"
    ],
    "description": "Affiche le nom du fichier actuel"
  }
}
```

**Variable utile :** `${TM_FILENAME}` → remplace automatiquement par le nom du fichier en cours.

---

## 5️⃣ Snippets spécifiques à un langage

- Python : `python.json`  
- JavaScript : `javascript.json`  
- HTML : `html.json`  

Placez ces fichiers dans le dossier User Snippets pour qu’ils soient chargés automatiquement.

---

## 6️⃣ Raccourcis utiles pour les snippets

- `Tab` : insérer le snippet après avoir tapé le préfixe  
- `Ctrl+Shift+P → Insert Snippet` : insérer un snippet via la palette  
- `Ctrl+Space` : activer l’autocomplétion et exécuter le snippet
