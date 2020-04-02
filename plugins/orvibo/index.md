# Orvibo

## Présentation

Ce plugin permet de piloter deux types de matériel Orvibo : AllOne et S20

Les AllOne sont des passerelles infrarouge.

Le AllOne propose un mode apprentissage qui permet de lui apprendre un code infrarouge.

Il dispose également d'un bouton sur le dessus qui est détecté par le plugin.

Il dispose également d'un émetteur/récepteur RF433 qui permet l'interconnexion avec les Switchs muraux Orvibo (début de support inclus)


Les S20 sont des prises Wifi.

Elles disposent d'un retour d'état dans Jeedom et visuel (led bleu/rouge suivant l'état) ainsi qu'un bouton physique en plus de l'API.

## Configuration

### Configuration du plugin

Le plugin ne comporte pas de configuration générale.

Les équipements Orvibo seront automatiquement créés sur découverte toutes les 10 mns. Un bouton de relance de la découverte est disponible sur la page de configuration.

### Configuration des prises S20

Chaque prise S20 présente est créée comme équipement Jeedom avec 3 commandes : on, off et status

Il n'y a pas besoin de créer d'autres commandes

### Configuration des AllOne

Chaque AllOne présent est créé en équipement Jeedom avec une seule commande par défaut : status

Cette information donne la dernière activité : code IR reçu ou boutton appuyé

La page AllOne dispose de deux boutons pour l'apprentissage de code IR. Si les deux sont verts, le AllOne est dans un mode apprentissage et créera des commandes pour chaque nouvelle valeur

On peut également activer l'apprentissage sans la création, seule l'information status changera

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, le plugin utilise une connexion via wifi au AllOne.

## Changelog

[Voir la page dédiée](changelog.md).
