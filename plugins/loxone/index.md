# Loxone

## Présentation

Loxone est un automate pour la maison connectée. Compatible avec le KNX, 1wire mais aussi les DI et DO standards ainsi qu'une multitude d'équipements accessibles par IP.

Le plugin Jeedom permet une interconnexion bidirectionnelle pour obtenir le meilleur des deux mondes.

## Configuration

La configuration générale nécessite de rentrer les variables propres au Miniserver Loxone : IP, utilisateur, mot de passe et port du Virtual Input UDP. On y trouve également l'url HTTP utilisable dans Loxone pour communiquer avec Jeedom.

Les connexions avec Loxone sont :

  - récupération de l'arbre des composants Loxone sur sauvegarde de la configuration et de façon journalière. Les commandes et équipements correspondants sont créés (uniquement ce que l'utilisateur peut voir). Uniquement les commandes digitales et analogiques sont disponibles.
  
  - les changements d'état sont récupérés par Jeedom en websocket (sous les mêmes conditions que plus haut, être accessibles à l'utilisateur et digital/analogique)
  
  - Jeedom peut envoyer des valeurs de commandes existantes sur trigger à Loxone (via le modal). Ceci utilise des commandes UDP vers Loxone en Virtual Input UDP.
  
  - Jeedom peut envoyer des commandes spécifiques à Loxone (via l'équipement Loxone). Ceci utilise des commandes UDP vers Loxone en Virtual Input UDP.
  
  - Loxone peut envoyer des commandes spécifiques à Jeedom via l'adresse indiquée sur la page de configuration (en Virtual Output HTTP). Il faut utiliser en contenu id="nom voulu" et value="valeur". Une info sera créée qui permet aussi de mettre des triggers Cmd actions et scénario.
  
Les commandes envoyées en UDP permettent côté Loxone de créer des commandes facilement à partir du moniteur (https://www.loxone.com/enen/kb/communication-with-udp/)

Pour utiliser les commandes HTTP pour envoyer vers Jeedom depuis Loxone, voir les Virtual Output (https://www.loxone.com/enen/kb/virtual-inputs-outputs/)

La référence de l'API Loxone est disponible dans leur documentation (https://www.loxone.com/enen/kb/api/)

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de votre Loxone. C'est donc sur le réseau local.

## Changelog

[Voir la page dédiée](changelog.md).
