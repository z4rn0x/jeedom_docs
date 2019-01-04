# Fake Roku

## Présentation

Ce plugin permet de simuler un Roku en local à Jeedom et ainsi d'être découvert et piloter par les télécommandes types Logitech Harmony ou Seven Hugs Smart.

## Configuration

Le plugin n'a pas de configuration générale et ne permet pas de créer d'équipements.

Un équipement est créé automatiquement avec l'ensemble des informations correspondant aux touches disponibles sur l'API Roku. Jeedom sera détecté comme un Roku par les scans de télécommandes multimédias compatibles.

Chaque commande est une information binaire qui passe à 1 quand elle est pressée sur une télécommande Roku (peu importe, appli mobile ou Logitech Harmony par exemple, du moment qu'elles utilisent l'API)

En plus de passer à 1, il est possible pour chaque commande de saisir 1 ou plusieurs commande action dans le champ prévu (en séparant avec && comme dans les autres plugins Jeedom le permettant). Chacune des actions sera activée sur pression de la touche.

Il y a aussi un champ scénario permettant de choisir un scénario à éxécuter.

Ce qui donne que la pression sur une touche permet : 

 l'info binaire passe à 1 + les commandes actions paramétrées s'éxécutent + le scénario paramétré se lance

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, le plugin créé justement une API compatible Roku en local

## Changelog

[Voir la page dédiée](changelog.md).
