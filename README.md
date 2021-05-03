# Registre de preuve de covoiturage

Site vitrine du Registre. https://covoiturage.beta.gouv.fr

## Mises à jour

### Ajouter un opérateur

> Pour cet exemple, utilisons _Maxicovoit_.

1. Dans le dossier `src/content/operateurs`, créer le fichier `maxicovoit.md` avec le contenu suivant :

```markdown
---
title: "Maxicovoit"
date: YYYY-MM-DDTHH:mm:ssZ   // mettre la date du moment
linked: false                // ou true si l'opérateur est connecté
logo: maxicovoit.png         // pas d'espaces et de majuscules dans le nom
link: https://example.com/
---
```

2. Commiter les modifications directement sur la branche `main` (en bas de page).
3. Uploader le logo `maxicovoit.png` dans `src/static/images/operateurs`. Une taille de 480x480 est suffisante.
4. Commiter les modifications directement sur la branche `main` (en bas de page).
5. Vérifier le bon déroulement du déploiement dans les [Actions](https://github.com/betagouv/preuve-covoiturage-vitrine/actions)

> Github ne permet pas de renommer les fichiers dans son interface. Il est nécessaire d'envoyer le fichier image avec le bon nom directement.

### Ajouter un territoire

> L'ajout des territoires sur la cartographie se fait à partir des comptes utilisateurs activés sur app.covoiturage.beta.gouv.fr.

###

Propriétés des fichiers Markdown

| nom | type | description |
| --- | --- | --- |
| title | `string` | Nom de l'opérateur ou du territoire. Utiliser des `""` |
| date | `date` | Date de création au format `YYYY-MM-DDTHH:mm:ssZ` |
| showTitle | `boolean` | Affichage du titre dans l'interface (`true` pour les territoires, omettre pour les opérateurs | 
| linked | `boolean` | `true` ou `false` pour les opérateurs liés ou en cours de liaison. Omettre pour les territoires |
| link | `string` | URL du site web |
| logo | `string` | nom du fichier, ex. `image.png` (png, jpg) supportés. 480x480 |

## Tech

Le site utilise le générateur de sites statiques [HUGO](https://gohugo.io/).
L'installation en local utilise Docker et Docker Compose.

### Installation

Cloner le dépôt et lancer la commande de développement.

### Développement

```shell
docker-compose up server
```

http://localhost:1313/

### Déploiement

```shell
docker-compose run hugo -e production
rsync -avz public/* rpc:www/home/
```

# License

DINUM, 2020-2021.

The source code is published under [Apache license 2.0](https://github.com/betagouv/preuve-covoiturage-vitrine/blob/main/LICENSE).
