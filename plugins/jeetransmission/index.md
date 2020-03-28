# Transmission, client bittorrent

## Présentation

Ce plugin permet de s'interfacer avec Transmission

Il récupère les informations du statut de Transmission (downloads en cours, terminés ...)

Il permet également de piloter Transmission (supprimer un torrent, purger un torrent ...)

## Configuration

Le plugin ne comporte pas de configuration générale.

Lorsqu'on crée un équipement, on doit fournir les éléments suivants :

  * adresse du serveur Transmission

  * utilisateur si requis

  * mot de passe si requis

  * adresse de consultation Transmission

Pour la liste des torrents présents, le plugin fournit :

  * ID : très important car c'est lui qu'il faut passer aux actions sur torrent

  * Nom : le nom du torrent

  * Statut : indique l'état

Concernant les statuts, voici les valeurs utiles :

  * 4 : téléchargement en cours

  * 6 : téléchargement terminé

  * 0 : en pause

### Exemple d'utilisation en scénario

Si vous souhaitez, par exemple, supprimer de Transmission tous les torrents terminés, vous pouvez utiliser un scénario comme celui-ci :

Dans un premier temps, on associe à une variable la valeur de la commande liste.

Ensuite, on analyse chaque élément (torrent) et si sa valeur de statut est 6 (terminé), on éxécute la commande d'arrêt avec ce torrent.


## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de votre Transmission. C'est donc sur le réseau local.

## Changelog

[Voir la page dédiée](changelog.md).
