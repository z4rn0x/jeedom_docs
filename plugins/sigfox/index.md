# Sigfox

## Présentation

Sigfox est un réseau pour objets connectés. Il propose une communication par module radio avec une portée de plusieurs kms.

Cette communication a deux limites : 140 messages par jour en montant (+2 descendants) et une taille de 12bytes.

C'est peu, mais c'est assez pour les objets connectés surtout quand ce sont des objets connectés sur batterie en pleine nature par exemple.

Le plugin ici ne permet pas d'utiliser une puce Sigfox actuellement. Il permet de récupérer les valeurs de données Sigfox par callback.

## Configuration

Le plugin ne comporte pas de configuration générale.

Il faut ajouter un équipement par donnée Sigfox à récupérer.

Sur l'équipement, on doit saisir l'identifiant unique Sigfox. L'adresse à saisir dans Sigfox est également présente.

Une fois l'identifiant enregistré, on copie l'adresse fournie par Jeedom dans la page de configuration Sigfox pour le callback.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, le plugin est appelé par Sigfox sur réception de données

## Changelog

[Voir la page dédiée](changelog.md).
