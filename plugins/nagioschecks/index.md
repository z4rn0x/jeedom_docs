# Check Nagios, éxécuter des checks Nagios dans Jeedom

## Présentation

Ce plugin permet d'obtenir le résultat de checks Nagios. Nagios est un logiciel de supervision disposant de scripts qui couvrent un très large domaine d'utilisations.

Les scripts peuvent être éxécutés en local ou via SSH (via check_by_ssh)

On peut par exemple récupérer l'état de disques durs, d'un RAID, de services ...

## Configuration

### Configuration du plugin

Le plugin ne comporte pas de configuration générale.

### Configuration équipement

Il faut ajouter un équipement par "unité" à superviser (comprendre pi, serveur ...)

Pour superviser un équipement distant il faut remplir les options de l'équipement suivantes (uniquement les distants) :

* Adresse IP

* Port SSH

* Identifiant

* Emplacement de la clef (uniquement les connexions par clef SSH sont supportées)

* Chemin des check Nagios sur la cible (en local ils sont intégrés)

##### Configuration commandes

Ensuite on ajoute une commande par élément à supervisier (état RAID, mysql, logs ...) qui corresponderont chacune à une commande à lancer (un check_***)

Chaque commande permet de paramétrer sa fréquence (5mn, 15mn ou 30mn)

On peut sélectionner si la commande est à éxécuter par SSH (dans ce cas, les options de l'équipement doivent être saisies)

On peut également avoir que le check soit éxécuter avec sudo

On peut également sélectionne la création automatique de commandes liées qui donnent le retour d'affichage, le résultat et les métriques

Dans la case commande on saisit le nom du check à lancer

Dans la case des options on saisit les options de ce check (voir les exemples)

#### Résultat de commande dans un scénario

Il est possible de récupérer la sortie Label du check dans un scénario en utilisant en bloc code :

$status # $cmd->getConfiguration('status');

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, le plugin éxécute des commandes locales ou par SSH.

## Changelog

[Voir la page dédiée](changelog.md).
