# Lecteur NFC

## Présentation

Ce plugin utilise un lecteur NFC/RFID ACR122U pour remonter les tags NFC/RFID lus

## Configuration

### Configuration du plugin

Il n'y a pas de configuration à faire

Il est possible d'activer ou non le service de détection

### Utilisation

Automatiquement les tags NFC seront remontés à Jeedom.

Si le plugin est en mode inclusion et qu'il n'existe pas d'équipement pour ce tag, un nouvel équipement est créé.

Une commande information est disponible pour chaque lecteur.

Leur statut est binaire. 1 pour une présence en cours, 0 si ils ne sont plus détectés.

### Utilisation du plugin sans Jeedom

Il est possible d'utiliser le plugin sans Jeedom dans 2 configurations :

  - avec un Linux, on placera alors le répertoire node sur celui-ci et on lance la commande "nodejs nfc.js $jeedomurl$ $nomlecteur$"
  on remplacera $jeedomurl$ par l'adresse indiquée par le plugin sur la page configuration, $nomlecteur$ par le nom qu'on souhaite donner à cette instance

  - avec un Tasker ou autre méthode, on devra appeler l'adresse donnée sur la page de configuration du plugin

## FAQ

> Est-ce qu'on peut utiliser en déporté ?

Oui, le plugin sur le déporté transmettra les résultats au Jeedom central.

>Est-ce que je peux utiliser tout type de lecteur NFC ?

Le plugin a été testé avec une version USB ACR122U, aucune garantie que d'autres lecteurs fonctionnent.

## Changelog

[Voir la page dédiée](changelog.md).
