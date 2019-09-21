# Routeur Asuswrt

## Présentation

Ce plugin permet de récupérer les informations de connexion des périphériques sur un routeur Asuswrt.

Il utilise la connexion SSH au routeur Asus pour récupérer la vitesse WAN et les infos des périphériques présents.

## Configuration

### Configuration générale

Le plugin nécessite de saisir 3 paramètres :

* Adresse IP du routeur
* Utilisateur SSH (normalement admin)
* Mot de passe (le même que via la conf par page web)

Il faut bien activer l'accès au SSH par l'adresse locale.

### Configuration d'un équipement

Le plugin ne comporte pas de configuration par équipement.

### Paramètres

L'équipement dispose de plusieurs commandes :

* Adresse MAC
* Adresse IP
* Hostname
* Connexion utilisée (ethernet ou wifi)
* RSSI ( égal à 0 si absent ou ethernet)
* Statut de connexion en texte
* Présence (binaire)

#### Installation d'apcupsd

Apcupsd doit être installé biensur, c'est lui qui sera interrogé

Il faut donc l'installer via la méthode appropriée sur votre système

#### Configuration de l'adresse d'écoute


## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Le plugin utilise une connexion SSH locale pour récupérer ses informations.

## Changelog

[Voir la page dédiée](changelog.md).
