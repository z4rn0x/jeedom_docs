# Ecocompteur Legrand, superviseur consommation électrique, eau et gaz

## Présentation

Ce plugin permet d'obtenir les informations de l'Ecocompteur Legrand (pinces Tor et compteurs à impulsions)

L'écocompteur dispose des informations suivantes :

* 5 prises Tor pour la consommation électrique par groupe

* 2 entrées impulsions pour l'eau ou le gaz

* 1 connectique TIC pour les compteurs intelligents


A la création d'un équipement Jeedom, toutes les consommations relevées par le compteur sont automatiquement créées et remontées en informations.

Une mesure est faite toutes les 2 minutes.


## Configuration

Le plugin ne comporte pas de configuration générale.

Il faut ajouter un équipement par compteur qu'on veut monitorer.

Pour chaque équipement, il suffit de renseigner son adresse et sauvergarder, les informations sont alors automatiquement créées.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, les informations sont obtenues localement du module.

## Troubleshooting

> Je n'ai pas d'informations qui remontent

Il faut bien créer un équipement et remplir l'adresse pour avoir les informations.

## Changelog

[Voir la page dédiée](changelog.md).
