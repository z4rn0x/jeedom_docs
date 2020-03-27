# Foobot

## Présentation

Ce plugin permet de récupérer dans Jeedom les données des capteurs Foobot

Sont récupérées les valeurs :

  - Température

  - Humidité

  - Dioxyde de Carbone

  - Composés Volatiles

  - Particules Fines

  - Global

## Configuration

Le plugin nécessite de saisir sa clef API dans la page de configuration du plugin.

La clef peut être récupérée sur la page http://api.foobot.io/apidoc/index.html#/

Les équipements sont créés automatiquement (un équipement par Foobot)

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, ce plugin utilise l'API Foobot et donc le Cloud. Il ne fonctionnera pas sans internet, il n'y a pas de moyen de récupérer les valeurs en local

## Changelog

[Voir la page dédiée](changelog.md).
