# Matrix Led Messenger

## Présentation

Ce plugin permet d'interconnecter Jeedom avec des afficheurs Smart Led Messenger ou Notif'Heure.

Il permet deux types d'interconnexions :

- Envoyer un message, y compris avec des options

- Définir le paramétrage permanent de l'afficheur en local en définissant un texte qui est rafraichi toutes les minutes.

Les mots clefs à utiliser dans le champ titre pour passer les options sont :

- intensity, speed, static et time (en minutes)

## Configuration

Le plugin ne comporte pas de configuration générale.

Sur chaque équipement il faut configurer :

  - l'adresse IP

  - les paramètres par défaut de vitesse, statique et luminosité

  - si l'on désire activer la gestion locale avec le message à afficher

Le champ "Message à afficher" prend les fonctions et les commandes informations en arguments, comme dans un scénario. Ce qui permet de rendre le texte dynamique. Il est rafraichi toutes les minutes.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, mais le plugin utilise l'API locale du Smart Led Messenger et permet de le déconnecter du Cloud.

## Changelog

[Voir la page dédiée](changelog.md).
