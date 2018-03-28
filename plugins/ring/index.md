# Ring, portier vidéo

## Présentation

Ce plugin permet d'interconnecter Jeedom avec vos équipements Ring.com (en reproduisant un navigateur web, il n'y a pas d'API officielle)

## Configuration

### Configuration du plugin

Il faut saisir votre compte Ring.com sur la page de configuration

### Configuration des équipements

Les équipements sont créés automatiquement à partir du compte Ring.com

Seuls les portiers sont créés et utilisés dans Jeedom, ils possèdent 3 commandes infos :

  * Mouvement : qui remonte les évènements de mouvement (identiques aux notifications disponible depuis l'application Ring)

  * Sonnerie : quand quelqu'un sonne (identiques aux notifications disponible depuis l'application Ring)

  * Batterie : qui donne le statut de la batterie (celui-ci est aussi visualisable dans la page Equipement, onglet Batteries de Jeedom)

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui le plugin utilise les API non officielles de Ring.com (il reproduit le comportement d'un navigateur web)

## Changelog

[Voir la page dédiée](changelog.md).
