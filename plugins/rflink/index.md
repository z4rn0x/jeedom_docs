# Rflink, passerelle multi fréquences

## Présentation

RFLink est une passerelle RF433 basée sur un Arduino Mega et un transceiver RF433

La passerelle reconnait en standard un grand nombre de protocoles et périphériques

Plus d'informations sur le site du projet Rflink :

http://www.nemcon.nl/blog2/

Pour se procurer le kit Rflink :

http://www.nodo-shop.nl/nl/21-rflink-gateway

La liste des périphériques compatibles :

http://www.nemcon.nl/blog2/devlist

## Configuration

### Configuration du plugin

Sur la page du plugin on peut :

  * Voir la version actuelle du firmware de la Gateway

  * Flasher et upgrader la version de firmware

  * Configurer le port USB de la Gateway ou indiquer si c'est une réseau

  * Entrer l'adresse réseau si c'est une Gateway réseau (avec le port d'écoute)

### Configuration de l'inclusion

Ce choix permet de décider si le contrôleur va créer des nouveaux équipements Jeedom pour les périphériques détectés et inconnus.

En le passant en "désactivé", aucun nouvel équipement n'apparaitra dans Jeedom.

Il est accessible sur la page équipement Rflink


### Configuration des nodes et leurs capteurs

Les équipements Jeedom sont automatiquement créés à l'envoi des informations des sondes.

De la même facon que les équipements sont automatiquement créés à l'arrivée de nouveaux périphériques, les capteurs des nodes sont automatiquement créés comme des "Informations" dans Jeedom ainsi que les commandes RECUES (il faut créer des commandes dans ce cas).


### Configuration des commandes des nodes

Les commandes ne sont pas toutes créées automatiquement.

Pour en créer une, il faut :

  * faire un ajout de commande action sur la page de l'équipement

  * puis il faut remplir le champ valeur en indiquant la bonne valeur SWITCH;CMD

  * SWITCH dans la colonne capteur

  * CMD dans la colonne information

Exemple : si on a une information créée en appuyant sur le bouton 2 avec en valeur "2;OFF". Il faut rentrer ce "2;OFF" dans la valeur de la commande créée

## FAQ

> Quel type de Gateway rflink est supporté ?

RFLink utilise un Arduino Mega, celui-ci doit être branché en USB sur un Jeedom (maître ou esclave)

>Qu'est-ce que rflink ?

RFLink est une Gateway pour les protocoles sans fil RF433

>Ma passerelle est branchée en USB sur un Jeedom satellite et le service ne démarre pas ?

Vérifier votre configuration réseau Jeedom dans Général->Administration->Configuration dans la partie Réseau

>Est-ce que je peux flasher le firmware de mon Rflink en ligne de commande ?

Oui, avec la commande ci dessous depuis votre Jeedom

/usr/bin/avrdude -v -v -v -p atmega2560 -c wiring -D -P /dev/ttyUSB0 -b 115200 -U flash:w:/usr/share/nginx/www/jeedom/plugins/rflink/resources/rflink/RFLink.cpp.hex:i

>Comment ajouter un store RTS (Somfy) ?

Vous devez commencer par appuyer sur un des boutons de la télécommande

Un équipement va être créé comprenant 4 commandes (pair, up, down, stop) et une info (statut)

Vous devez à partir de ce moment, mettre votre volet en mode appairage (en appuyant sur le bouton adéquat de la télécommande)

Puis appuyer sur le bouton "Tester" de la commande PAIR

>Aucun équipement ne se crée

Sur la page de configuration, vous pouvez vérifier que le service du plugin est démarré et connecté.

Allez voir dans la section logs de Jeedom : catégorie rflink et éventuellement la catégorie API

>Comment se créer mes équipements?

A réception de trames, l'équipement et ses commandes sont créées

>Je suspecte un problème de connexion avec ma Gateway

Sur la page de configuration du plugin, vous avez une note d'information qui donne le statut du service du plugin Jeedom et également le statut de connexion de celui-ci à la Gateway

>Mes logs montrent que j'ai bien de la communication de périphériques, mais je n'ai pas d'équipement qui apparait dans Jeedom

Vérifier votre configuration réseau dans Jeedom. Vous devez bien avoir rempli tous les champs de votre adresse interne. Protocole, adresse et complément url surtout (si vous êtes sur une installation Jeedom DIY, vous devez avoir /jeedom dans "complément")

## Changelog

[Voir la page dédiée](changelog.md).
