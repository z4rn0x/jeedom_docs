# OpenBR, reconnaissance faciale

## Présentation

Ce plugin permet de comparer des screenshots avec une image de référence pour reconnaitre une personne.

## Configuration

### Configuration du plugin

Le plugin ne comporte pas de configuration générale.

Il faut ajouter un équipement par visage à reconnaître.

Sur chaque équipement il faut uploader la photo de référence.

Ensuite il y aura 2 commandes de créées. Une action message pour passer en paramètre l'emplacement d'une image à comparer. Et une action info numérique qui donne le résultat.

L'information numérique : plus sa valeur est élevée, plus la probabilité est haute de reconnaissance

### Utilisation du plugin

La commande action permet de passer un screenshot de caméra pour analyse

On peut également l'utiliser pour passer en titre directement une adresse d'image locale

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de votre Loxone. C'est donc sur le réseau local.

## Changelog

[Voir la page dédiée](changelog.md).
