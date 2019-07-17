# Hikvision

## Présentation

Ce plugin permet de lire les trames émises par les caméras Hikvision en cas d'évènement.

Il permet de récupérer :

- la détection de mouvement

- la détection de ligne

- la perte de vidéo

- la vidéo aveugle

- l'alarme locale

Attention, toutes les commandes ne sont pas disponibles sur toutes les caméras

Le protocole existe dans certaines caméras "clone" Hikvision sans garantie

POur être sur de bien recevoir les notifications, pensez à vérifier vos configurations Hikvision et que les différentes détection sont bien actives pour votre modèle

## Configuration

Le plugin ne comporte pas de configuration générale.

Il faut configurer l'adresse, l'utilisateur et le mot de passe de la caméra Hikvision dans l'équipement. A noter qu'un équipement dans le plugin Caméra est créé si la Hikvision n'y est pas encore présente.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, le plugin est en connexion directe avec le Doorbird

## Changelog

[Voir la page dédiée](changelog.md).
