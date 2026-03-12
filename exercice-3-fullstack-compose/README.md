# Exercice 3 - Architecture complete avec reseaux

Objectif: decrire une architecture front + api + base de donnees dans un seul fichier Compose, avec reseaux dedies, build local et image nommee.

## Contexte

Vous devez mettre en place une architecture composee:
- d'un service `web` construit localement
- d'un service `api` construit localement
- d'un service `db` base sur `postgres:15`

Le front ne doit parler qu'a l'API. La base de donnees ne doit pas etre exposee vers l'hote et ne doit etre accessible que via le reseau backend.

## Fichiers fournis

- `web/Dockerfile`
- `web/index.html`
- `web/nginx.conf`
- `api/Dockerfile`
- `api/index.js`
- `api/package.json`
- `.env.example`

## Travail a faire

1. Creer un fichier `.env` a partir de `.env.example` et completer les valeurs.
2. Declarer une architecture Compose avec `web`, `api` et `db`.
3. Faire les choix de configuration necessaires pour:
   - construire les services applicatifs et nommer les images produites
   - externaliser la configuration sensible via le fichier `.env`
   - exposer uniquement les services utiles vers l'hote
   - conserver les donnees de la base
   - isoler correctement les communications reseau
4. Lancer la stack puis verifier son fonctionnement.
5. Nettoyer l'ensemble des ressources creees.

Les commandes doivent etre fournies dans un fichier separe `COMMANDS.md`.

## Questions de reflexion

- Pourquoi `api` doit-il etre connecte a deux reseaux dans cette architecture ?
`api` est connecté aux deux réseaux pour servir d'intermédiaire : le front l'atteint via le réseau `frontend`, et `api` contacte la DB via le réseau `backend`. Cela évite d'exposer la DB côté `frontend`.
- Quel interet de combiner `build` et `image` sur un meme service ?
Combiner `build` et `image` permet de construire localement tout en donnant un nom d'image stable (utile pour push/CI ou pour référencer l'image ailleurs).
- Pourquoi la base ne doit-elle pas etre publiee avec `ports` dans ce cas ?
La DB ne doit pas être publiée (`ports`) pour éviter qu'elle soit accessible directement depuis l'hôte, elle doit rester sur le réseau `backend`.


## Criteres de validation

- Les trois services sont declares dans un seul fichier Compose
- Les reseaux `frontend` et `backend` sont utilises correctement
- Au moins un service combine `build` et `image`
- La base de donnees reste interne a la stack
