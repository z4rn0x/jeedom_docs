# Héliotrope : lever, coucher, zénith, azimuth et altitude du soleil

## Présentation

Ce plugin permet d'obtenir l'azimuth et l'altitude solaire pour être utilisé dans des scénarios

Il permet également de récupérer l'heure du coucher et lever du soleil avec un calcul local (sans API) et paramétrable

Il permet de lancer des tâches aux heures calculées

## Configuration

Le plugin permet en configuration générale de paramétrer la fréquence du cron.

Il faut ajouter un équipement et sélectionner l'équipement Localisation et Trajets (geotrav) qui servira pour le calcul.

Ce plugin utilise une information venant de la conf Jeedom ou du plugin Localisation et Trajets (geotrav) afin de réutiliser une localisation déjà existante.

Un autre paramètre est disponible pour paramétrer l'angle qu'on souhaite utiliser pour le calcul du coucher et lever du soleil uniquement (par défaut 90.58, ce qui est utilisé en général)

Le plugin apporte différentes informations, certaines sont calculées quotidiennement, d'autres sont rafraichies par le cron dédié.


Informations à rafraichissement quotidien (le calcul est fait à 3h du matin, sur démarrage de la box Jeedom ou sur sauvegarde de l'équipement) :

  - lever du soleil

  - coucher du soleil

  - durée de la journée (entre lever du soleil et coucher du soleil)

  - zénith du soleil

  - aube astronomique (lever du soleil -18°)

  - aube nautique (lever du soleil -12°)

  - aube civile (lever du soleil -6°)

  - crépuscule astronomique (lever du soleil +18°)

  - crépuscule nautique (lever du soleil +12°)

  - crépuscule civil (lever du soleil +6°)

Les informations restantes sont recalculées à la fréquence paramétrée sur la configuration plugin :

  - azimuth solaire

  - altitude solaire

  - phase du jour numérique

  - phase du jour texte

  Les valeurs de la phase du jour sont :

    - 0 : Nuit

    - 1 : Jour

    - 2 : Aube Civile

    - 3 : Aube Nautique

    - 4 : Aube Astronomique

    - 5 : Crépuscule Civil

    - 6 : Crépuscule Nautique

    - 7 : Crépuscule Astronomique

## Exemple

Définitions :
  - Azimut : angle absolu par rapport au nord (le nord étant à 0° et les valeurs augmentant en tournant dans le sens des aiguilles d'une montre, lorsqu'on regarde le sol depuis le ciel)
  - Altitude : angle sous lequel on voit le soleil, par rapport à l'horizon qui est la référence.

Il y a deux notations possibles pour l'azimut : azimut (de 0 à 180 puis de -180 à -0) ou azimut360 (de 0 à 360). Vous utiliserez celui qui vous convient le plus.

Exemples :
  Le soleil se couche à l'ouest, soit 270°.
  Le soleil à la verticale parfaite aura une altitude de 90°, un soleil qui a disparu sous l'horizon aura une altitude négative.

### Comment utiliser les valeurs azimut/altitude dans un scénario ?

Voici un exemple, basé sur l'excellente photo de Masterfion :

![Illustration](Heliotrope_sample.png?raw=true "Illustration")

Je reprends l'exemple du volet 4 et j'ai rajouté un volet 5 sur un autre bâtiment...

#### Volet 4 :

La perpendiculaire au volet 4 (ou à la façade qui le contient) a un azimut de 250°. Cela signifie que la tangente à la façade (ligne qui court le long de la façade) a un azimut de (250°-90°) 160° (ou 250+90=340° si on part dans l'autre sens).

Cela veut dire que lorsque le soleil se trouve à l'azimut 160°, ses rayons sont parallèles à la façade. S'il progresse encore plus vers l'ouest, ses rayons vont commencer à taper sur la façade et donc entrer par la fenêtre. Il faudrait donc fermer la fenêtre à partir d'un azimut solaire de 160°. Le soleil ne va jamais passer de l'autre côté de la façade dans ce cas (l'autre côté est à 340° et le soleil sera couché avant à environ 270°) donc on laissera probablement le volet fermé.

#### Volet 5 :

La façade contenant le volet 5 a une perpendiculaire ayant un azimut de 170°. Cela veut dire que la façade a un axe (une tangente) 80°-> 260°.

Dans ce cas, dès le lever du soleil, il éclaire la façade (sous un angle de 10°). Il faut donc fermer le volet 5 dès le lever du soleil.

On peut utiliser l'altitude pour décider qu'il est levé : regardez la valeur de l'altitude sur le plugin lorsqu'il se lève et commence à éclairer et notez-la comme valeur de déclenchement du scénario.

Sinon, utilisez un théodolite qui permet de relever des angles par rapport à l'horizontale.


Le soleil va se déplacer vers l'ouest et cessera d'éclairer la façade lorsqu'il arrivera à l'azimut (170°+90°) 260°. Là il sera possible d'ouvrir à nouveau le volet 5 pour profiter des dernières lueurs du jour (260°, c'est presque un soleil couché).

### Comment utiliser les valeurs de lever/coucher du soleil dans un scénario ?

Héliotrope calcule ces informations quotidiennement. Les utiliser en tant que déclencheurs seuls, aura pour effet de déclencher le scénario à 3h00 du matin (ou au reboot), pas vraiment l'effet souhaité.

Il faut utiliser le déclencheur en combinaison avec une condition A.

On pourra utiliser time_op pour ajouter 30mn à l'heure du coucher par exemple, comme sur la capture suivante

![Illustration](Heliotrope_sample2.jpg?raw=true "Illustration")

Il est possible également de déclencher alors un scénario différent pour garder d'autres moyens de contrôles comme la commande manuelle.

Exemple :

  - un scénario héliotrope avec :

    * une info d'horaire du plugin en déclencheur

    * un bloc A avec l'heure de l'aube qui déclenche un scénario "ouverture des volets"

    * un bloc A avec l'heure du crépuscule qui déclenche un scénario "fermeture des volets"

    * on peut imaginer différents blocs A pour différents scénarios. Par exemple en utilisant différents crépuscules, le nautique pour les volets, le civil pour les lampes.

  - les scénarios "ouverture des volets" ou "fermeture des volets" pourront être déclenchés directement par l'app aussi pour garder un contrôle manuel.


## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, le plugin fait le calcul en interne par rapport aux coordonnées.

>Est-ce que le plugin s'appuie sur des plugins tiers ?

Oui, il utilise un équipement du plugin geotrav

>Je n'ai pas d'informations qui remontent

Il faut bien créer un équipement et remplir les informations du lieu pour lequel on souhaite avoir les horaires.

>Est-ce que je peux me servir des heures calculées pour déclencher des scénarios ?

Oui, il suffit de saisir la commande voulue comme déclencheur puis de créer une condition A #commande##heure##voulue#

## Changelog

[Voir la page dédiée](changelog.md).
