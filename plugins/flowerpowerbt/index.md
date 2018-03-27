# Parrot Plants

## Présentation

Ce plugin utilise une connexion bluetooth fonctionnelle sur Jeedom pour se connecter aux flower power et pots et remonter les informations.

Il n'est pas nécessaire de créer les équipements, le plugin créer automatiquement les Flower Power trouvées.

Sans clef bluetooth le service récupère les valeurs de l'API Parrot

## Configuration

### Configuration du plugin

Pour récupérer les informations des Parrot Flower Power, vous devez configurer votre compte Parrot sur la page de conf.

Il vous faut :

* votre compte de l'appli mobile

* votre mot de passe de l'appli mobile

* votre compte API

* votre clef API

Pour obtenir la clef API direction cette page : https://api-flower-power-pot.parrot.com/api_access/signup

Sur un Jeedom où il est activé, toutes les heures il récupère les infos de Parrot.

Si le service Bluetooth est activé, il fera une synchro par heure en bluetooth. Veuillez à bien avoir une clef dédiée pour cet usage, les Flower ne pouvant fonctionner avec une clef partagée (avec beacon ou sniffer par exemple)

### Utilisation d'un déporté sans jeedom

Attention, n'utilisez cette méthode que si vous êtes en mesure de vous débrouiller avec les quelques explications ici.

Il faut configurer le plugin avant toutes

Ensuite copier le répertoire node sur le Linux cible

Lancer './install.sh' en tant que root sur la cible

Là on pourra vérifier le fonctionnement avec './bridge display'

Il est possible d'ajouter './bridge background 60' au démarrage ensuite pour lancer la récupération dès le boot


## FAQ

> Est*ce que le plugin s'appuie sur des API tiers ?

Oui il récupère les informations de l'API Parrot et transmet les données des équipements BLE vers leur API aussi.

## Changelog

[Voir la page dédiée](changelog.md).
