# Imperihome

## Présentation

Le plugin Imperihome permet:
 * la mise à disposition d'une API "ISS" pour Imperihome (récupération des données de JeeDom et demandes d'actions)
 * l'utilisation de l'API Control d'Imperihome pour intéragir avec le logiciel Imperihome installé sur un périphérique (non intégré à l'heure actuelle)

## Configuration

### Plugin
L'activation du plugin nécessite un pré-requis: avoir renseigné la configuration réseau dans le menu Général -> Administration -> Configuration.

Celle-ci permet en effet au plugin de déterminer le chemin d'accès de l'API ISS qu'il faudra renseigner dans Imperihome.

Une fois le plugin activé (menu Général -> Plugins -> Imperihome), une section "Configuration" apparait.

A ce moment là, le plugin détermine automatiquement l'adresse à renseigner dans Imperihome:

image::../images/plugin_config.jpg[Configuration du plugin]

### Configuration d'Imperihome
Sous imperihome, aller dans Paramètres -> Mes Systèmes, puis Ajouter un système. Sélectionner "Imperihome Standard System", puis rentrer l'URL donnée par le plugin dans "URL de Base API Locale".

Si vous souhaitez accéder depuis l'exterieur, configurer également l'URL Externe en l'adaptant à votre installation.

Cliquer sur suivant et terminer. Si aucun équipement ne s'affiche, c'est normal pour le moment, il faut aller sélectionner quels équipements vous souhaitez remonter vers Imperihome.

### Sélection des équipements à transmettre
Rendez-vous dans la page Plugins -> Imperihome, puis dans l'onglet "Configuration ISS".

image::../images/ISSConfig.jpg[Configuration du plugin]

Vous pouvez ici sélectionner les équipements à transmettre, et visualiser le type d'équipement automatiquement détecté.

Une fois les équipements sélectionnés, cliquer sur "Sauvegarder". Sous Imperihome, il se peut que l'équipement ne remonte pas immédiatement. Pour forcer la mise à jour, cliquer sur la double flèche rotative en haut à droite de l'écran sous Imperihome.

### Détermination automatique du type d'équipement
Dans le mesure du possible, le plugin essaie de reconnaitre les équipements et de leur donner un type "Imperihome" adapté.
En automatique, le plugin transforme les commandes de type "info" en un équipement.

Si on prend en exemple, une prise de courant télécommandée et qui remonte les informations de consommation, celle-ci aura deux commandes de type "info": Etat et Conso.

Le plugin va alors créer 2 équipements: un de type "devSwitch" (pour Etat) et l'autre de type "devElectricity" pour Conso.

### Détermination manuel du type d'équipement
!! Attention: modifier le type d'un équipement alors que celui-ci est configuré dans Imperihome peut faire planter l'application.

!! Je vous recommande de supprimer l'équipement dans Imperihome avant de modifier son type dans Jeedom.

Pour accéder au mode avancé, il faut activer le Mode Expert de Jeedom.
Un onglet "Mode avancé" est alors disponible.

image::../images/ISSAdvancedConfig.jpg[Configuration du plugin]

Vous retrouvez ici les équipements configurés manuellement.

Vous pouvez les modifier ou supprimer, ou en créer un nouveau.

Lorsque vous cliquez sur "Ajouter un équipement" ou Modifier, la fenêtre qui s'ouvre permet de configurer l'équipement.

image::../images/ISSEqAdvancedConfig1.jpg[Configuration du plugin]

Il faut alors configurer la commande support: celle-ci correspond au nom de l'équipement qui s'affichera sur Imperihome.

Ensuite, il faut sélectionner le type d'équipement (https://imperihome.zendesk.com/hc/en-us/articles/202088308-ImperiHome-Standard-System-API-definition[se reporter à la doc Imperihome]).

Ensuite, vous pouvez configurer chaque paramètre et action.

image::../images/ISSEqAdvancedConfig2.jpg[Configuration du plugin]

Pour les paramètres, il faut soit rentrer manuellement une valeur, soit sélectionner une commande de type Info.

Pour les actions, il faut nécessairement sélectionner une commande de type Action.

Prenons l'exemple d'une prise télécommandée. Disons que sous Jeedom, elle possède deux commandes Info (Etat et Consommation) et deux commandes Action (Allumer et Eteindre).

Il faudra alors selectionner le type "Standard On/Off switch".

.Puis:
* paramètre Status: selectionner la commande Etat
* paramètre Energy: selectionner la commande Consommation
* action setStatus:

   - pour le 0: selectionner la commande Eteindre

   - pour le 1: selectionner la commande Allumer

Sauvegarder la configuration, puis réactualiser la liste des équipements sous Imperihome.

Il y a une subtilité pour le type MultiSwitch et son action SetChoice. Si une commande est renseignée, alors elle sera appelée en lui passant comme paramètre la valeur sélectionnée dans Imperihome. Si aucune commande n'est renseignée, alors le plugin recherchera une commande ayant comme nom la valeur sélectionnée dans Imperihome au sein du même équipement que la commande support.

## Paramétrage

### Explication

Le système de détection automatique se base sur un certain nombre de critères afin de déterminer le type le plus adapté à Imperihome.

Ci-dessous, vous trouverez les différents critères pour pouvoir avoir une détection optimale.

### Définition des critères

###= Actionneurs
[panel,primary]
.Interrupteur [DevSwitch]
--
.Conditions:
* La commande est de type Binaire et il y a des commandes de type Action dans l'équipement

.ou
* Il s'agit d'une commande de type Action
--

[panel,primary]
.Variateur de lumière [DevDimmer]
--
.Conditions:
* Le widget de la commande est "Light"

.ou
* La commande est de type Numeric et a comme unité "%" ainsi que des commandes de type Action dans l'équipement
--

[panel,primary]
.Serrure [DevLock]
--
Pas de détection automatique sur ce type. Utiliser le mode avancé.
--

[panel,primary]
.Lampe RGB [DevRGBLight]
--
.Conditions:
* Il existe au moins une commande de type Couleur dans l'équipement
--

[panel,primary]
.Volet [DevShutter]
--
.Conditions:
* La commande est liée au plugin Store

.ou

* Le widget de la commande est "Store"
--


###= Détecteurs et Capteurs
[panel,primary]
.Capteur de CO2 [DevCO2]
--
.Conditions:
* Le type de la commande est "Binaire" et le nom de la commande contient "Fumée" ou "Smoke"

.ou
* La commande est de type Numeric et a comme unité "ppm"
--

[panel,primary]
.Détecteur de CO2 [DevCO2Alert]
--
.Conditions:
* Le type de la commande est "Binaire"

.et
* Le nom de la commande est "Co"
--

[panel,primary]
.Détecteur d'ouverture [DevDoor]
--
.Conditions:
* Le widget de la commande est "Door", "Baie", "Window" ou "Porte_garage"

.ou
* Le nom de la commande contient "Etat" et le nom de l'équipement est "Fenetre" ou "Porte"
--

[panel,primary]
.Compteur d'énergie [DevElectricity]
--
.Conditions:
* La commande est de type Numeric et a comme unité "w" ou "kwh"
--

[panel,primary]
.Compteur d'eau [DevFlood]
--
.Conditions:
* La commande est de type Numeric et a comme unité "m3"
--

[panel,primary]
.Capteur d'humidité [DevHygrometry]
--
.Conditions:
* Le nom de la commande contient "Humidité"
--

[panel,primary]
.Capteur de luminosité [DevLuminosity]
--
.Conditions:
* La commande est de type Numeric et a comme unité "lux"
--

[panel,primary]
.Détecteur de mouvement [DevMotion]
--
.Conditions:
* Le widget de la commande est "Presence"

.ou
* La commande est liée au plugin Alarme
--

[panel,primary]
.Capteur de bruit [DevNoise]
--
.Conditions:
* La commande est de type Numeric et a comme unité "dB"
--

[panel,primary]
.Capteur de pression [DevPressure]
--
.Conditions:
* La commande est de type Numeric et a comme unité ""
--

[panel,primary]
.Capteur de pluie [DevRain]
--
.Conditions:
* La commande est de type Numeric et a comme unité "mm/h" ou "mm"
--

[panel,primary]
.Détecteur de fumée [DevSmoke]
--
.Conditions:
* Le widget de la commande est "Fire"
--

[panel,primary]
.Capteur de température [DevTemperature]
--
.Conditions:
* La commande est de type Numeric et a comme unité "°C"
--

[panel,primary]
.Capteur de température et humidité [DevTempHygro]
--
.Conditions:
* Le nom de la commande contient "Humidité"

.et
* Une commande du même équipement a comme unité "°C", et est indiquée comme "A Transmettre"



.OU
* La commande a comme unité "°C"

.et
* Une commande du même équipement a comme nom "Humidité", et est indiquée comme "A Transmettre"
--

[panel,primary]
.Capteur d'UV [DevUV]
--
.Conditions:
* Le nom de la commande contient "UV"
--

[panel,primary]
.Capteur de vent [DevWind]
--
.Conditions:
* La commande est de type Numeric et a comme unité "km/h"
--

###= Scénarios
[panel,primary]
.Scénario [DevScene]
--
.Conditions:
* Il s'agit d'un scénario
--

###= Autres
[panel,primary]
.Equipement générique [DevGenericSensor]
--
.Conditions:
* La commande est de type Numeric, a comme unité "%" et il n'y a pas de commandes de type Action dans l'équipement

.ou
* La commande est de type Binaire et il n'y a pas de commandes de type Action dans l'équipement

.ou
* Il n'a pas été possible de déterminer un autre type: type retourné par défaut
--

[panel,primary]
.Caméra [DevCamera]
--
.Conditions:
* La commande est liée au plugin Caméra
--

[panel,primary]
.Selecteur de choix [DevMultiSwitch]
--
.Conditions:
* La commande est liée au plugin Présence

.ou
* La commande est liée au plugin Alarme (sélection du mode)
--

[panel,primary]
.Thermostat [DevThermostat]
--
* La commande est liée au plugin Thermostat
--

## Controle ImperiHome

Il est possible de créer des équipements qui représentent des clients Imperihome, cela permet de les contrôler par api

Il est nécessaire de saisir l'adresse IP (avec le port) en configuration

Ensuite les commandes suivantes seront disponibles :

  - Lancer une page : ouvre une page sur l'Imperihome, il faut saisir l'ID de la page dans le message

  - Lancer une camera : ouvre une caméra en plein écran, il faut saisir l'ID de la caméra dans le message

  - Lancer la reconnaissance vocale : fait passer Imperihome en reconnaissance Vocale

  - Lire un message TTS : lit le message envoyé, si un titre est saisi, il doit être numérique de 0 à 100 et sera le volume en %

  - Réveiller : permet de réveiller la tablette/téléphone d'Imperihome


## FAQ

> Ou trouver le lien à renseigner dans ImperiHome ?

Le lien de l'API a configurer dans Imperihome est donné dans la page de configuration.

## Changelog

[Voir la page dédiée](changelog.md).
