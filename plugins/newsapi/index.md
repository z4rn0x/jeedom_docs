# News API

## Présentation

News API est un site permettant de récupérer des informations suivant différents critères.

## Configuration

Chaque équipement créé va correspondre à une information (pas Jeedom, une information journalistique)

Ainsi, si vous voulez récupérer les 3 dernières, il faudra 3 équipements en définissant bien l'index.

Pour chaque équipement, il vous faudra [la clef API](https://newsapi.org/register)

Ensuite, vous pourrez choisir entre la catégorie "Gros Titres" ou "Générales"

Sur chaque équipement, vous définissez l'index que vous voulez récupérer. Par exemple la dernière news sera 1, l'avant dernière 2 ... Ca permet avec la duplication de facilement créer 3 équipements pour les 3 dernières news.

Ensuite, pour la catégorie "gros titres", vous devez choisir un pays et une catégorie (ou des sources). Il est également possible d'ajouter du mot clef à chercher.[Voir aussi](https://newsapi.org/docs/endpoints/top-headlines)

Pour la catégorie générale, il faut définir la langue puis vous pouvez choisir du mot clef, des domaines à restreindre ou exclure des sources. [Voir aussi](https://newsapi.org/docs/endpoints/everything)

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API du site News API.

## Changelog

[Voir la page dédiée](changelog.md).
