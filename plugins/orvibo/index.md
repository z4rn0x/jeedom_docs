# Orvibo

## Présentation

Ce plugin permet de piloter deux types de matériel Orvibo : AllOne et S20

Les AllOne sont des passerrelles infrarouge.

Le AllOne propose un mode apprentissage qui permet de lui apprendre un code infrarouge.

Il dispose également d'un bouton sur le dessus qui est détecté par le plugin.

Il dispose également d'un émetteur/récepteur RF433 qui permet l'interconnexion avec les Switchs muraux Orvibo (début de support inclu)


Les S20 sont des prises Wifi.

Elles disposent d'un retour d'état dans Jeedom et visuel (led bleu/rouge suivant l'état) ainsi qu'un bouton physique en plus de l'API.

## Configuration

### Configuration du plugin

Le plugin ne comporte pas de configuration générale.

Les équipements Orvibo seront automatiquement créer sur découverte toutes les 10mn. Un bouton de relance de la découverte est disponible sur la page de configuration.

### Configuration des prises S20

Chaque prise S20 presente est creer comme equipement Jeedom avec 3 commandes : on, off et status

Il n'y a pas besoin de creer d'autres commandes

### Configuration des AllOne

Chaque AllOne present est creer en equipement Jeedom avec une seule commande par defaut : status

Cette information donne la derniere ativite : code IR recu ou boutton appuye

La page AllOne dispose de deux boutons pour l'apprentissage de code IR. Si les deux sont verts, le AllOne est dans un mode apprentissage et creera des commandes pour chaue nouvelle valeur<

On peut egalement activer l'apprentissage sans la creation, seule l'information status changera

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, le plugin utilise une connection via wifi au AllOne.

## Changelog

[Voir la page dédiée](changelog.md).
