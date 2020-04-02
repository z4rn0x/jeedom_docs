# Matrix Display

## Présentation

Ce plugin permet d'interconnecter Jeedom avec des afficheurs Smart Led Messenger, Notif'Heure ou Awtrix.

Il permet deux types de commandes actions :

- Envoyer un message, y compris avec des options

- Définir le paramétrage permanent de l'afficheur en local en définissant un texte qui est rafraichi toutes les minutes (Smart Messenger et Notif'Heure).

- Paramétrer la couleur d'affichage (Awtrix)

Les mots clefs à utiliser dans le champ titre pour passer les options sont :

- intensity, speed, static et time pour le Smart Led Messenger

- intensity, type, txt, flash et time pour le Notif'Heure

- bri, color, mood, gamemode, game pour l'Awtrix

Pour le Notif'Heure, en cas de présence du DHT22, les commandes infos température, humidité, température ressentie, point de rosée et indice de confort sont créées

## Configuration

Le plugin ne comporte pas de configuration générale.

Sur chaque équipement, il faut configurer :

  - l'adresse IP (avec le port pour Awtrix 2)

  - le type (Smart Led Messenger, Notif'Heure, Awtrix 1 et 2)

  - les paramètres par défaut de vitesse, statique et luminosité pour le Smart Led Messenger

  - les paramètres par défaut de luminosité, effet, flash, texte avant notif pour le Notif'Heure

  - si l'on désire activer la gestion locale avec le message à afficher

Le champ "Message à afficher" prend les fonctions et les commandes informations en arguments, comme dans un scénario. Ce qui permet de rendre le texte dynamique. Il est rafraichi toutes les minutes.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, mais le plugin utilise l'API locale du Smart Led Messenger et permet de le déconnecter du Cloud.

> Ou puis-je trouver la documentation du Notif'Heure ?

https://byfeel.info/documentation-notifheure/

## Changelog

[Voir la page dédiée](changelog.md).
