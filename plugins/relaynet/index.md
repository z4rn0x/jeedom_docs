# RelayNet, carte relais 8 ports en ethernet

## Présentation

Ce plugin permet de piloter une carte générique 8 relais en ethernet qu'on trouve sur ebay et autres épiceries chinoises

Où l'acheter ?

Chercher "8-Channel-Relay-Network-IP-Relay-Web-Relay-Dual-Control-Ethernet-RJ45-interface" sur ali ou thanksbuyer

Prévoir une alim type chargeur de 12V / 1A

## Configuration

### Configuration du plugin

Le plugin ne comporte pas de configuration générale.

Il faut configurer l'adresse et le port de la carte après avoir ajouter un équipement.

Les commandes (8 relais off/on) et informations (8 statut relais et 8 input) sont créées automatiquement.

### Configuration de la carte relais

Les informations utiles pour se connecter à la carte par défaut :

  * Adresse IP :192.168.1.166

  * Port TCP: 1234

  * Utilisateur: admin

  * MDP: 12345678

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de votre carte. C'est donc sur le réseau local.

## Changelog

[Voir la page dédiée](changelog.md).
