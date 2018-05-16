# Check Nagios, exécuter des checks Nagios dans Jeedom

## Présentation

Ce plugin permet d'obtenir le résultat de checks Nagios. Nagios est un logiciel de supervision disposant de scripts qui couvrent un très large domaine d'utilisations.

Les scripts peuvent être exécutés en local ou via SSH (via check_by_ssh).

On peut par exemple récupérer l'état de disques durs, d'un RAID, de services ...

## Configuration

### Configuration du plugin

Le plugin ne comporte pas de configuration générale.

### Configuration équipement

Il faut ajouter un équipement par "unité" à superviser (comprendre pi, serveur ...).

Pour superviser un équipement distant il faut remplir les options de l'équipement suivantes (uniquement les distants) :

* Adresse IP

* Port SSH

* Identifiant

* Emplacement de la clef privée (sont uniquement supportées les connexions par clef SSH)

* Chemin des checks Nagios sur la cible (en local ils sont intégrés)

##### Configuration commandes

Ensuite on ajoute une commande par élément à superviser (état RAID, mysql, logs ...) qui correspondra chacune à une commande à lancer (un check_***).

Chaque commande permet de paramétrer sa fréquence (5mn, 15mn ou 30mn).

On peut sélectionner si la commande est à exécuter "Par SSH" (dans ce cas, les options de l'équipement doivent être saisies).

On peut également exécuter le check "Avec Sudo".

On peut également sélectionner la création automatique de commandes liées qui donnent le retour d'affichage, le résultat et les métriques.

Dans la case "Check" on saisit le nom du check à lancer.

Dans la case "Options" on saisit les options de ce check (voir [les exemples](exemples.md)).

#### Résultat de commande dans un scénario

Il est possible de récupérer la sortie Label du check dans un scénario en utilisant en bloc code :

$status # $cmd->getConfiguration('status');

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, le plugin exécute des commandes locales ou par SSH.

## Changelog

[Voir la page dédiée](changelog.md).
