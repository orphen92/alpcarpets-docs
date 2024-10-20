# Proposition Technique

Ce document est la solution technique proposée par Sylvain Bousselier dans le cadre de refonte du site [Alpcarpets](https://alpcarpets.com/en/)  

## Besoin
L'entreprise est dans une démarche de refonte de son site en plusieurs étapes.

Liste des contraintes de l'étape 1

- [x] Le site a une version mobile
- [x] Le site a des contraintes SEO
- [ ] Le site a des contraintes Accessibilité
- [ ] Le site a des contraintes Ecoconception
- [ ] Le site a une base de donnée
- [ ] Le site utilise des api
- [x] Le site est évolutif technologiquement
- [x] Le contenu du site doit être mis à jour
- [x] Le site est multilangue

## Proposition générale
Plutôt que de voir la construction des pages de facon statique, il serait plus avisé de les construire grâce à des composants paramétrables représentant chacun un élément du site final.

L'idée est d'avoir un fichier json par page pour chaque url du site.

Cela permettra plusieurs choses:

- [x] Création aisée de nouvelles pages 
- [x] Ajout d'un CMS facilement
- [x] Debug facilité
- [x] Personnalisation accrue
- [x] Evolution technique simplifiée/rapide du site 

## Technologies utilisées

- [x] Node
- [x] React
- [x] Nextjs
- [x] Zod
- [x] Json
- [x] Html
- [x] Css
- [x] typescript

## Solution technique
Chaque url du site sera associée à un fichier json portant le même nom et qui sera une représentation des données de la page.

par exemple:
    https://alpcarpets.com/en/collections --> https://alpcarpets.com/api/en/collections.json

## Pages (json)

Le json contiendra des informations générales sur la page

Le json sera dupliqué dans un dossier par langue
    https://alpcarpets.com/api/en/collections.json
    https://alpcarpets.com/api/fr/collections.json
    https://alpcarpets.com/api/es/collections.json

``` json
{
    "id": "id de la page",
    "title": "titre de la page",
    "meta": {
        "title": "titre du navigateur",
        "description": "meta description"
    },
    "header": [
        "subNav": {...}
        "mainNav": {...} 
    ],
    "footer": [
        "Social": [
            {
                "name": "facebook",
                "link": ""
            }
        ]
    ],
    "componentList": [
        {
            "type": "type-carrousel",
            "id": "id unique du carrousel",
            "behavior": {
                "speed": 1.5,
                "controls": true
            },
            "slides": [
                {
                    "title": "slide 1",
                    "images": [...]
                }
            ]
        }
    ]
}
```

## Composants (json)
Chaque composant a une propriété `type`, ce qui permettra de le repérer dans le tableau `componentList` et de l'associer au code associé à ce composant.
Un schéma de validation sera associé avec zod pour typer les valeurs du Json par rapport au type des propriétés associées à chaque composant.

Les composants peuvent avoir un paramètre ici nommé `behavior` pour correspondre aux besoins fonctionnels ou de maquette.

Ces paramètres seront typés afin d'être bien identifiés et qu'il soit plus facile de savoir ce qu'il est possible de faire sur chaque composant.

``` json
{
    "type": "type-carrousel",
    "id": "id unique du carrousel",
    "behavior": {
        "speed": 1.5,
        "controls": true
    },
    "slides": [
        {
            "title": "slide 1",
            "images": [...]
        }
    ]
}
```


## Construction des pages 
Dans ma conception de cette construction technique, je pense qu'il serait intéressant de partir sur des composants de structure en grille, ce qui permettra d'afficher nimporte quel composant où on le souhaite dans la page et d'ajouter des options pour définir le nombre de colonne par ligne.

Par exemple: l'option 1 colonne affichera tous les composants à 100% de l'espace disponible, 2 colonnes afficheront tous les composants à 50% de l'espace disponible, etc.
Ci-dessous, nous avons une grille paramétrée sur 2 colonnes (50% chaque colonne):

| Colonne 1                | Colonne 2            |
| -----------              | ----------           |
| `Composant Title`        | `Composantimage`     |



``` json
{
    "type": "type-grid",
    "id": "id unique de la grille",
    "behavior": {
        "layout": "2cols",
    },
    "gridComponents": [
        {
            "type": "type-title",
            "id": "id unique du title",
            "title": "titre"
        },
        {
            "type": "type-Image",
            "id": "id unique de l'image",
            "url": "uURLrl AWS"
        }
    ]
}
```