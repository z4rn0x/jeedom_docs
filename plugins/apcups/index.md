# Onduleurs APC

## Présentation

Ce plugin permet de récupérer les informations d'onduleurs APC et également d'être averti sur leurs évènements.

Il utilise apcupsd en dépendance (installer pendant l'activation du plugin) et permet de gérer un onduleur APC en USB ou distant.

Les informations fournies sont :

* Charge : le % de charge de l'onduleur par rapport à sa puissance
* Batterie : le % de charge de la batterie de l'onduleur
* Courant Entrant : la tension du courant d'alimentation de l'onduleur
* Modèle : le modèle d'onduleur
* Statut : le statut de l'onduleur
* Temps sur batterie : la durée d'autonomie disponible
* Voltage pile : tension de la pile
* Evènement : tout évènement détecté par le service apcupsd qui est transmit en push à Jeedom

## Configuration

### Configuration générale

Le plugin ne comporte pas de configuration générale.

A noter que lorsque le plugin est activé, il effectue deux actions :

* Installation et configuration de apcupsd pour gérer un onduleur USB
* Création d'un équipement pour déclarer l'onduleur USB créé

### Configuration d'un équipement

Comme indiqué plus haut, un premier équipement est créé à l'activation. Il est fonctionnel pour un onduleur USB local.

Vous pouvez ajouter d'autres équipements si vous disposez d'autres onduleurs sur le réseau par exemple.

Le plugin se trouve dans la catégorie Monitoring.

### Paramètres

L'équipement dispose de 3 paramètres :

* Adresse : l'adresse de connexion pour obtenir les informations APC (127.0.0.1 par défaut)
* Port : le port d'écoute du service apcupsd (par défaut 3551)
* Puissance : la puissance de l'onduleur (nécessaire pour avoir accès à la consommation)

Attention : il faut bien saisir une adresse ip et pas un nom pour l'adresse, celle ci est utilisée pour identifier qui émet un event en push

Pour la puissance, elle est facilement identifiable dans le nom du modèle (Back-Up 550 USB par exemple, 550 est la puissance)

### Utilisation

L'équipement dispose d'un widget associé pour le tableau de bord.

La consommation est disponible pour être intégrée dans le plugin Energie par exemple via un calcul entre la charge et la puissance de l'onduleur.

L'information event sera utile pour déclencher des scénarios, ainsi que le statut.

La durée de batterie peut être un bon complément dans les scénarios déclenchés sur statut par exemple.

### Configuration d'un onduleur accessible via le réseau

#### Installation d'apcupsd

Apcupsd doit être installé biensur, c'est lui qui sera interrogé

Il faut donc l'installer via la méthode appropriée sur votre système

#### Configuration de l'adresse d'écoute

Dans le fichier /etc/apcupsd/apcupsd.conf, vous devez vérifier le paramètre NISIP afin que ce soit bien l'adresse de la machine sur le réseau et pas 127.0.0.1 (qui serait non interrogeable)

NISIP 192.168.0.100

####  Modification d'apccontrol pour activer le push

Dans le fichier /etc/apcupsd/apccontrol, vous devez ajouter en début une ligne pour appeler Jeedom sur les évènements.

Copier celle qui est présente sur Jeedom

#### Configuration dans Jeedom

Maintenant il n'y a plus qu'à ajouter un équipement et renseigner l'adresse que vous avez remplie dans la configuration

### Evènements fournis par apcupsd


Voici la liste des évènements que peux envoyer apcupsd

* annoyme : When a shutdown is scheduled, and the time specified on the ANNOYME directive in the apcupsd.conf file expires, this event is generated.

* changeme : When apcupsd detects that the mains are on, but the battery is not functioning correctly, this event is generated. It is repeated every x hours.

* commfailure : This event is generated each time the communications line with the computer is severed. This event is not detected on dumb signaling UPSes.

* commok : After a commfailure event is issued, when the communications to the computer is re-established, this event will be generated.

* doreboot : This event is depreciated and should not be used.

* doshutdown : When the UPS is running on batteries and one of the limits expires (time, run, load), this event is generated to cause the machine to shutdown.

* emergency : Called for an emergency system shutdown. (What triggers such a shutdown is unclear...) After completing this event, apcupsd will immediately initiate a doshutdown event.

* failing : This event is generated when the UPS is running on batteries and the battery power is exhausted. The event following this one will be a shutdown.

* loadlimit : This event is generated when the battery charge is below the low limit specified in the apcupsd.conf file. After completing this event, apcupsd will immediately initiate a doshutdown event.

* powerout : This event is generated immediately when apcupsd detects that the UPS has switched to batteries. It may be due to a short powerfailure, an automatic selftest of the UPS, or a longer powerfailure.

* onbattery : This event is generated 5 or 6 seconds after an initial powerfailure is detected. It means that apcupsd definitely considers the UPS to be on batteries. The onset of this event can be delayed by the ONBATTERYDELAY apcupsd.conf configuration directive.

* offbattery : This event is generated when the mains return only if the onbattery event has been generated.

* mainsback : This event is generated when the mains power returns after a powerout condition. The shutdown event may or may not have been generated depending on the parameters you have defined and the length of the power outage.

* remotedown : This event is generated on a slave machine when it detects either that the master has shutdown, or that a onbattery situation exists and the communications line has been severed.

* runlimit : This event is generated when the MINUTES value defined in the apcupsd.conf file expires while in a power fail condition. The MINUTES is the remaining runtime as internally calculated by the UPS and monitored by apcupsd. After completing this event, apcupsd will immediately initiate a doshutdown event.

* timeout : This event is generated when the TIMEOUT value defined in the apcupsd.conf file expires while in a power fail condition. It indicates that the total time in a power failure has been exceeded and the machine should be shutdown. After completing this event, apcupsd will immediately initiate a doshutdown event.

* startselftest : This event is generated when apcupsd detects a self test by the UPS. Normally due to the 6 second onbattery delay default time, self test events are not detected.

* endselftest : This event is generated when the end of a self test is detected.

* battdetach : This event is generated when apcupsd detects that the UPS battery has been disconnected.

* battattach : This event is generated when apcupsd detects that the UPS battery has been reconnected after a battdetach event.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Le plugin utilise apcupsd pour récupérer ses informations.

## Troubleshooting

> Je n'ai pas d'informations qui remontent

Il faut bien créer un équipement et remplir les informations.

## Changelog

[Voir la page dédiée](changelog.md).
