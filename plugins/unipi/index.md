# Unipi

## Présentation

La carte UniPi dispose de :

8x relais 5A
14 entrées digitales 5-24V qui peuvent servir en impulsions, résistance de pull-up logiciel, debounce aussi (8 pour IPX800 + 4 impulsions)
2 entrée analogiques 0-10V
1 sortie analogique 0-10V (inexistant sur l'IPX)
Port 1-wire pour la température + humidité

Cartes d'extension disponibles également (actuellement par exemple, carte 8 relais)
8 cartes d'extension possibles par UniPi (72 relais pour un Pi donc)

## Configuration

Il est nécessaire de fournir les informations pour accéder à la carte UniPi via l'API Evok :

  Adresse de l'API Evok (locale à Jeedom ou non)

La sauvegarde d'un équipement permet de créer automatiquement les informations/commandes de la carte Unipi.

Les 14 DI, 2 AI, 8 DI, 1 AO sont créer par exemple.

Si vous ajoutez des sondes 1wire, une simple sauvegarde devrait créer les informations relatives.

L'équipement complet est visible sur le doNotShowNameOnDashboard

Les informations sont recues en temps réel de la carte via un websocket connecté à l'Unipi. Un cron de fond permet de sécuriser l'état en refaisant la requête auprès de l'API Evok

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, le websocket de l'Unipi. C'est une connexion sur le réseau local.

## Changelog

[Voir la page dédiée](changelog.md).
