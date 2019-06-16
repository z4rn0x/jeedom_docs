# Google Home Local

## Présentation

Ce plugin a pour but de gérer vos Google Home et par extension vos Chromecast.

Le plugin permet d'envoyer des médias vers vos Google Home et Chromecast.

Pour les Google Home, il permet aussi de récupérer les alarmes et timers, l'activation du mode silencieux, le scan bluetooth

## Configuration

Le plugin ne dispose pas de configuration générale.

Pour chaque équipement, il faut indiquer si c'est un Google Home ou Chromecast, ainsi que son IP.

Les commandes sont créées automatiquement.

## Commandes

Les commandes suivantes sont communes aux Google Home et Chromecast (car elles utilisent la fonctionnalité Chromecast du Google Home) :

Stop lecture

Pause lecture

Reprise lecture

Définir volume lecture

Lire une phrase

Jouer un Fichier


Ouvrir une URL

Commande Scénario

Radio

Sons locaux


Les Google Home ont des commandes spécifiques qui s'appuient sur leur API local non officielle :

Alarmes informations brutes

Alarme existante

Alarme existante ce jour

Heure de la prochaine Alarme

Timers informations brutes

Timer existant

Durée original du timer (en mn)

Heure du prochain Timer

Volume Alarmes (avec Définir Volume Alarme)

Etat Notification (avec Notification On, Notification Off)

Rafraichir

Redémarrer

Et les périphériques Bluetooth scannés

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de votre Google Home. C'est donc sur le réseau local.

## Changelog

[Voir la page dédiée](changelog.md).
