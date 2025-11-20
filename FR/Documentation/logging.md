# Logging

## Introduction à la journalisation (logging) en Python

La journalisation est une technique essentielle en développement logiciel qui permet d'enregistrer des informations sur l'exécution d'un programme. Ces informations, appelées "logs", peuvent vous aider à :

- **Déboguer votre code** : Identifier les erreurs et les problèmes dans votre programme.
    
- **Surveiller l'activité de votre application** : Comprendre comment votre programme est utilisé et identifier les tendances d'utilisation.
    
- **Auditer les événements importants** : Enregistrer les actions des utilisateurs, les transactions, les changements d'état, etc.
    

## Utilité du logging

- **Développement et maintenance** : Facilite la compréhension du comportement du programme et la résolution des problèmes.
    
- **Analyse des performances** : Permet d'identifier les goulots d'étranglement et d'optimiser le code.
    
- **Sécurité** : Aide à détecter les activités suspectes et à analyser les incidents de sécurité.
    

## Exemples pour différents types de messages

En Python, la bibliothèque `logging` offre différentes fonctions pour enregistrer des messages avec différents niveaux de gravité :

- `debug()` : Informations détaillées pour le débogage.
    
- `info()` : Messages informatifs sur l'exécution normale du programme.
    
- `warning()` : Avertissements sur des événements potentiellement problématiques.
    
- `error()` : Erreurs qui empêchent le programme de fonctionner correctement.
    
- `critical()` : Erreurs critiques qui peuvent entraîner l'arrêt du programme.
    

## Exemple de code

```python
import logging

# Configuration du logging (niveau de journalisation, format des messages, etc.)
logging.basicConfig(filename='mon_programme.log', level=logging.DEBUG,
                    format='%(asctime)s - %(levelname)s - %(message)s')

# Exemples de messages de log
logging.debug('Ceci est un message de débogage.')
logging.info('Le programme a démarré avec succès.')
logging.warning('Une valeur inattendue a été détectée.')
logging.error('Une erreur s\'est produite lors de l\'accès au fichier.')
logging.critical('Erreur critique : impossible de se connecter à la base de données.')
```

Ce code va :

- Créer un fichier `mon_programme.log`.
    
- Enregistrer tous les messages de niveau DEBUG ou supérieur.
    
- Formater les messages avec la date, l'heure, le niveau de gravité et le message lui-même.
    

## Conseils

- Choisissez le niveau de journalisation approprié en fonction de vos besoins.
    
- Utilisez un format de message clair et informatif.
    
- Envisagez d'utiliser un système de rotation des logs pour éviter que les fichiers de log ne deviennent trop volumineux.
    
- Utilisez la journalisation de manière stratégique pour ne pas surcharger les fichiers de log avec des informations inutiles.
    

## Gestion des erreurs avec try-except

Il est important de gérer les erreurs dans votre code pour éviter les plantages et fournir des informations utiles pour le débogage. Le bloc `try-except` permet de capturer les exceptions et d'enregistrer des messages d'erreur :

```python
try:
    # Code qui peut potentiellement générer une erreur
    resultat = 10 / 0  # Division par zéro
except ZeroDivisionError as e:
    logging.error('Erreur : %s', e)
```

## Journalisation des dates et des utilisateurs

Vous pouvez personnaliser le format des messages de log pour inclure des informations supplémentaires, comme la date, l'heure et le nom de l'utilisateur :

```python
logging.basicConfig(format='%(asctime)s - %(user)s - %(levelname)s - %(message)s')
```