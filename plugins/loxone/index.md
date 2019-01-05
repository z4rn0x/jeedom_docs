# Loxone

## Présentation

Loxone est un automate pour la maison connectée. Compatible avec le KNX, 1wire mais aussi les DI et DO standards ainsi qu'une multitude d'équiepements accessible par IP.

Le plugin Jeedom permet une interconnexion bidirectionnelle pour obtenir le meilleur des deux mondes.

## Configuration

La configuration générale nécessite de rentrer les variables propre au Miniserver Loxone : IP, utilisateur et mot de passe. On y trouve également l'url HTTP utilisable dans Loxone pour communiquer avec Jeedom.

Les connexions avec Loxone sont :

  - récupération de l'arbre des composants Loxone sur sauvegarde et daily. Les commandes et équipements correspondant sont créés
  
  - les changements d'état sont récupérés par Jeedom en websocket
  
  - Jeedom peut envoyer des valeurs de commandes existantes sur trigger à Loxone (via le modal)
  
  - Jeedom peut envoyer des commandes spécifiques à Loxone (via l'équipement Loxone)
  
  - Loxone peut envoyer des commandes spécifiques à Jeedom via l'adresse indiquée sur la page de configuration (en Virtual Output HTTP). Il faut utiliser en contenu id="nom voulu" et value="valeur". Une info sera créée qui permet aussi de mettre des triggers Cmd actions et scénario.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de votre Loxone. C'est donc sur le réseau local.

## Changelog

[Voir la page dédiée](changelog.md).
