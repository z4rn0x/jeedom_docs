# SSH Commander, éxécution de commandes SSH

## Présentation

Ce plugin permet de simplement créer un équipement par host SSH et d'y ajouter une commande par action que l'on souhaite exécuter

Par exemple, pour votre Pi Squeezebox, un équipement avec 4 commandes : reboot, shutdown, service squeezelite status et service squeezelite restart

## Configuration du plugin

Le plugin ne comporte pas de configuration générale.

Pour chaque équipement, il faut configurer les paramètres de connexion ssh (ip/hostname, user, password ou clef)

Ensuite, on ajoute une commande par action voulue (reboot, service ...)

Pour chaque action créée, il est possible de cocher l'option permettant de récupérer le retour et en faire une commande information

## Changelog

[Voir la page dédiée](changelog.md).
