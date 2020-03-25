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

Il est possible par équipement de sélectionner un plugin dans lequel il est présent, l'équipement du plugin sera alors activé/désactivé automatiquement suivant sa présence sur le routeur.

Les seuls plugins pris en charge sont : Xiaomi Home, Shelly et Hikvision

### Paramètres

L'équipement dispose de plusieurs commandes :

* Adresse MAC
* Adresse IP
* Hostname
* Connexion utilisée (ethernet ou wifi)
* RSSI ( égal à 0 si absent ou ethernet)
* Statut de connexion en texte
* Présence (binaire)
* Statut accès Internet
* Interdire l'accès Internet
* Autoriser l'accès Internet
* Wake On Lan

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Le plugin utilise une connexion SSH locale pour récupérer ses informations.

## Changelog

[Voir la page dédiée](changelog.md).
