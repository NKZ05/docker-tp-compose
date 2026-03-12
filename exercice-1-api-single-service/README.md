# Exercice 1 - Premier service avec Docker Compose

Objectif: lancer un premier service web avec Docker Compose a partir d'une image Nginx personnalisee.

## Contexte

Vous devez decrire un service web simple dans un fichier `compose.yaml` au lieu d'utiliser une commande `docker run`.
Un dossier applicatif minimal vous est fourni pour construire une image Nginx capable de servir une page HTML statique.

## Fichiers fournis

- `web/Dockerfile`
- `web/index.html`

## Attendu

Votre rendu doit permettre:

- de construire une image basee sur Nginx
- de copier la page fournie dans l'image
- de lancer le service avec Docker Compose
- d'afficher correctement la page sur `http://localhost:8080`
- d'observer puis d'arreter proprement la stack

Les commandes doivent etre fournies dans un fichier separe `COMMANDS.md`.

## Questions de reflexion

- Quel est l'avantage de decrire ce service dans un fichier plutot qu'avec `docker run` ?
Parce que la configuration devient déclarative, reproductible et versionnée. Compose orchestre le build, le réseau et les dépendances.
- Quelle difference entre le nom du service et le nom du conteneur cree ?
Le service est une clé dans le fichier Compose; Compose crée un (ou plusieurs) conteneur(s) dont le nom est dérivé du projet, du service et d'un index. Le nom du service est stable dans le fichier, le nom du conteneur peut inclure le nom du dossier/projet.
- Que permettent `docker compose ps` et `docker compose logs` pendant le diagnostic ?
`ps` montre l'état et les ports exposés des conteneurs gérés par la stack. `logs` affiche la sortie standard/erreur pour diagnostiquer.

## Criteres de validation

- Le fichier `compose.yaml` est valide et lisible
- L'image est construite a partir des fichiers fournis
- Le service `web` demarre correctement
- Le service est accessible sur `http://localhost:8080`
- La stack est arretee et supprimee proprement
