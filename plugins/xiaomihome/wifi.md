# Appliances Wifi Xiaomi

## Création des équipements Wifi

Pour les équipements Wifi supplémentaires supportés, il faut faire un ajout manuel. Ces informations sont nécessaires :
* Il faut renseigner leur **adresse IP**.
* Sélectionner le **type d'équipement** dans le menu déroulant.
* Renseigner le **token** : Pour l'obtenir, il suffit de cliquer sur le bouton bleu "Récupérer les infos". Dans le cas où le token récupéré est une suite de 0 seulement ou de f seulement, il faut alors le récupérer manuellement à l'aide d'une des procédures ci-dessous.

## Récupérer le token d'un équipement manuellement

Cinq méthodes existent :
* la première avec l'outil **[Mi Toolkit](https://github.com/ultrara1n/MiToolkit)** qui va récupérer tous les tokens dans votre application Mi Home. Cela nécessite un Android avec le mode Debug USB activable.
* Les deux suivantes sont basées sur une **récupération de la base de données de Mi Home**, une pour **Android**, l'autre pour **iPhone**.
* La quatrième permet de récupérer les tokens en utilisant une version modifiée de Mi Home (**uniquement sur Android**).
* La dernière avec Packet Sender à l'initialisation de l'appliance

### 1ère méthode : MiToolkit

Pour télécharger l'outil : [Cliquez ici](https://github.com/ultrara1n/MiToolkit/releases).
Il vous faut aussi une version Mi Home compatible, les dernières posent problème : [ApkMirror](https://www.apkmirror.com/apk/xiaomi-inc/mihome/mihome-5-0-19-release/)

* Activez **ADB** sur votre téléphone (dans les options développeur).
* Lancez le fichier **MiToolkit.exe** en tant qu'admin, sur votre ordinateur.
* Passez l'application en **anglais** via le menu avec le drapeau allemand. L'application se ferme, il faut la **relancer**.
* Choisissez **Extract Token**.
* Choisissez **Extract Token** à nouveau. Laissez-le faire la sauvegarde sur le PC et **ne mettez pas de mot de passe**.
* Les **tokens** apparaissent dans la fenêtre.

### 2ème méthode (Android) : aSQLiteManager

Via **aSQLiteManager**, on peut ouvrir la base de Mi Home. Attention, un téléphone rooté peut être nécessaire (merci _Gouzou_ pour la technique).

Les tokens sont dans la table **devicerecord** dans `/data/data/com.xiaomi.smarthome./databases/miio2.db`.

Ce fichier, si il est transférable sur PC, devrait pouvoir être édité avec d'autres logiciels également.

### 3ème méthode (iPhone)

Merci _pierre_ pour cette technique :

* Faites une **sauvegarde** de l'iPhone avec iTunes.
* Ouvrez la sauvegarde avec **[iPhoneBackup Viewer](http://www.imactools.com/iphonebackupviewer/)**. Si votre sauvegarde est cryptée, il faudra passer par la version payante.
* Dans `Raw Data/com.xiaomi.mihome`, il y a plusieurs fichiers `.sqllite`, il faut extraire `votreuserid_mihome.sqlite`.
* Ouvrez le fichier **sqlite** avec un viewer sqlite, par exemple **[DB Browser](http://sqlitebrowser.org)**.
* Cliquez sur **Ouvrir une base de données** puis **Parcourir les données** et enfin choisissez la table **ZDEVICE**.
* Tout à droite, il doit y avoir une colonne **ZTOKEN** avec tous les tokens de vos périphériques Xiaomi.
* La dernière version de l'application Mi Home sur iPhone stocke les tokens sous un format encrypté. Pour le decrypter, aller **[sur ce site](http://aes.online-domain-tools.com/)** et saisir les informations suivantes : 
  * Input type : text
  * Input text (hex): la clé de 96 caractères précédemment récupérée dans la colonne **ZTOKEN**
  * Selectbox Plaintext / Hex: Hex
  * Function: AES
  * Mode: ECB
  * Key (hex): 00000000000000000000000000000000
  * Selectbox Plaintext / Hex: Hex
  * Cliquer sur le bouton `Decrypt`. Votre token sont les deux premières lignes sur le bloc de droite. Ces deux lignes devrait contenir votre token de 32 caractères.

### 4ème méthode (Android)
* Autoriser les sources inconnues:
 L’installation d’applications hors Google Play Store nécessite de modifier les paramètres du téléphone, de façon à autoriser l’installation d’applications en provenance de sources dites « inconnues ».
 Sur son téléphone : Paramètres → onglet Général → Sécurité puis cochez Sources inconnues.
* Installer l’appli mi-home modifiée:
 Nous allons installer une version modifiée de mi home qui affiche en clair son token directement dans l’appli. Simple et efficace.
 Télécharger l’appli mihome modifiée sur son téléphone android: (07/12/18 5.4.37)

 https://drive.google.com/drive/folders/18OyC78peggCdiMmmT7i5bpvpdMJl1Ec1?usp=sharing

* L’installer, l’ouvrir se connecter avec son identifiant xiaomi afin de récupérer sa configuration habituelle.
* Récupérer son token:
 Sur la nouvelle appli mi home : Aller sur l'appliance, menu configuration / général settings / informations sur le réseau
 Deux lignes nous intéressent : l’adresse IP locale du robot et le token
 Notez précieusement et sans erreur ces informations. Quand c’est bon, vous pouvez désinstaller mi home modifié pour réinstaller la version officielle
 
### 5ème méthode (Packet Sender Tool)
During setup of Mi Home devices the device tokens an be retrieved by sending a ping command to the device. This method uses a tool called Packet Sender which you will need to download. Choose the portable version which does not require installation.
• Download the portable version of Packet Sender.
• Reset the device following the instructions from the device manual, this usually means holding one or two buttons for 10 seconds. This will reset all device settings including the Wi-Fi settings.
• After reset the device will create a it's own Wi-Fi network. This network will have a name related to the device and is used for configuring the device but will also allow us to retrieve the token. Connect to this Wi-Fi network with your computer which has Packet Sender running.
• Open Packet Sender and enter the following details.
o HEX: 21310020ffffffffffffffffffffffffffffffffffffffffffffffffffffffff
o IP: 192.168.8.1
o Port: 54321
o Protocol dropdown: UDP
• Click send and the device will respond with an answer which contains the unique device token. In the last 16 bytes (32 characters) of the devices response is the device token. Copy and save it somewhere.
• Disconnect your computer from the devices network, you can now use the Mi Home app to setup the device and connect it to your Wi-Fi network.

## Configuration des équipements Wifi

Cette section traite des équipements Wifi additionnels. Il n'est pas question de Yeelight ou de la gateway Aqara.

* **Xiaomi Mi Robot Vacuum** : online, statut, batterie, aspiration (force + slider, attention au delà de 77 vous dépassez le mode turbo), surface nettoyée, durée nettoyage, état des erreurs, puissance aspiration, démarrer, arrêter, pause, retour socle, fonction spot, "où es-tu ?", rafraichir.
* **Xiaomi Smart Mi Air Purifier (y compris Pro ou V2 avec écran)** : statut, qualité d'air, humidité, température, filtre, vitesse, buzzer (on/off), led (action dessus aussi), démarrer/arrêter (avec les différents modes disponibles).
* **Xiaomi Smart Ultrasonic Humidifier** : statut, mode, humidité, humidité cible (+slider de set), température, buzzer (statut + activation), led (statut + activation), démarrer/arrêter (avec les différents modes disponibles).
* **Xiaomi Smart Air Quality Monitor PM2.5 Detector** : qualité d'air, batterie, rafraichir.
* **Xiaomi Mi Power Strip Wifi** : on, off, statut, température, Intensité, puissance, rafraichir.
* **Xiaomi Mi Power Plug Wifi** : on, off, statut, utilisation, voltage, charge voltage, charge puissance, puissance consommée, rafraichir.
* **Xiaomi Philips Eyecare Smart Lamp** : statut, on/off, luminosité (+slider), eyecare (statut, scènes + différents modes disponibles).
* **Xiaomi Philips Ceiling** : statut, on/off, luminosité (+slider), couleur de blanc (info+cmd), Auto CCT (statut+cmd), scènes (statut + activation scènes).
* **Xiaomi Philips E27 (marche aussi pour les E14, à valider sur les spots)** : statut, on/off, luminosité (+slider), couleur de blanc (info+cmd), Auto CCT (statut+cmd), scènes (statut + activation scènes).
* **Xiaomi Mi Electric Rice Cooker** : non implémenté en l'état.
* **Ventilateur** : statut, température, humidité, buzzer (statut + activation), led (statut + activation), démarrer/arrêter (avec les différents modes disponibles), info vitesse et vitesse naturelle, rotation (et les commandes pour la paramétrer, tourner).
