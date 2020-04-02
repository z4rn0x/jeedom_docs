# OpenSprinkler, gestionnaire d'arrosage de jardins

## Présentation

Ce plugin permet de communiquer avec un OpenSprinkler.

Il permet de récupérer les informations à disposition du OS mais également de lui envoyer des commandes.

## Configuration

### Configuration du plugin

Dans la configuration du plugin, il faut renseigner :

  * l'adresse de l'OpenSprinkler (sous la forme ip:port)

  * le mot de passe à utiliser

Les informations sur le firmware et matériel sont disponibles sur la page de configuration après avoir rentré les renseignements

### Equipement pour le controleur

Le contrôleur est créé dans Jeedom avec les commandes suivantes :

  * Etat du contrôleur (binaire) qui indique si il est actif

  * Les actions d'activation et désactivation

  * Décalage pluie en cours (binaire) qui indique si l'OS est en mode pluie active

  * Fin décalage pluie (timestamp) qui indique l'heure de fin de la pluie

  * Programmer un délai pluie en heures (message) : cette action est à utiliser en scénario avec une valeur numérique pour le décalage pluie (c'est un nombre d'heures)

  * Etat du capteur pluie (binaire) qui donne le statut du capteur pluie si il est présent

  * Reboot action qui permet de rebooter

  * Reset les stations (coupe toutes les stations en cours et en attente)

### Equipements pour les stations

Pour chaque station, un équipement est créé avec les commandes suivantes :

  * Station activée (binaire) qui indique si elle est active (ne pas confondre avec le statut)

  * Les actions d'activation/désactivation

  * Ignore la pluie (binaire) qui indique que la station ne tiendra pas compte du statut de pluie

  * Les actions d'activation/désactivation

  * Mode séquentiel (binaire)

  * Les actions d'activation/désactivation

  * Connexion à Master 1 (binaire)

  * Les actions d'activation/désactivation

  * Connexion à Master 2 (binaire)

  * Les actions d'activation/désactivation

## FAQ

> Est*ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de votre OpenSprinkler. C'est donc sur le réseau local.

## Changelog

[Voir la page dédiée](changelog.md).
