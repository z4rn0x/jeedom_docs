# Xiaomi Wifi Appliances

## Creation of WiFi equipment

For additional WiFi equipment supported, a manual addition must be made. This information is necessary :
* You must enter their ** IP address **.
* Select the ** type of equipment ** from the drop-down menu.
* Fill in the ** token **: To obtain it, just click on the blue button "Retrieve info". In the case where the token retrieved is a sequence of only 0 or only f, it must then be retrieved manually using one of the procedures below.

## Retrieve the token of a device manually

Six methods exist (the last one is the easiest):
* the first with the tool ** [Mi Toolkit] (https://github.com/ultrara1n/MiToolkit) ** which will recover all the tokens in your Mi Home application. This requires an Android with the USB Debug mode activated.
* The next two are based on a ** recovery from the Mi Home database **, one for ** Android **, the other for ** iPhone **.
* The fourth allows to recover tokens using a modified version of Mi Home (** only on Android **).
* The fifth with Packet Sender at the initialization of the appliance
* The sixth uses a version 5.4.49 of Mi Home which gives the tokens in a log file

### 1st method: MiToolkit

To download the tool: [Click here] (https://github.com/ultrara1n/MiToolkit/releases).
You also need a compatible Mi Home version, the latest are problematic: [ApkMirror] (https://www.apkmirror.com/apk/xiaomi-inc/mihome/mihome-5-0-19-release/)

* Activate ** ADB ** on your phone (in developer options).
* Launch the file ** MiToolkit.exe ** as admin, on your computer.
* Switch the application to ** English ** via the menu with the German flag. The application closes, you must ** relaunch **.
* Choose ** Extract Token **.
* Choose ** Extract Token ** again. Let him do the backup on the PC and ** don't put a password **.
* The ** tokens ** appear in the window.

### 2nd method (Android): aSQLiteManager

Via ** aSQLiteManager **, you can open the Mi Home database. Attention, a rooted phone may be necessary (thank you _Gouzou_ for the technique).

The tokens are in the table ** devicerecord ** in `/ data / data / com.xiaomi.smarthome. / Databases / miio2.db`.

This file, if it is transferable to PC, should be editable with other software as well.

### 3rd method (iPhone)

Thank you _pierre_ for this technique:

* Make a ** backup ** of the iPhone with iTunes.
* Open the backup with ** [iPhoneBackup Viewer] (http://www.imactools.com/iphonebackupviewer/) **. If your backup is encrypted, you will have to go through the paid version.
* In `Raw Data / com.xiaomi.mihome`, there are several` .sqllite` files, you must extract `yourreuserid_mihome.sqlite`.
* Open the ** sqlite ** file with a sqlite viewer, for example ** [DB Browser] (http://sqlitebrowser.org) **.
* Click on ** Open a database ** then ** Browse the data ** and finally choose the table ** ZDEVICE **.
* On the far right, there should be a ** ZTOKEN ** column with all the tokens of your Xiaomi devices.
* The latest version of the Mi Home application on iPhone stores tokens in an encrypted format. To decrypt it, go ** [on this site] (http://aes.online-domain-tools.com/) ** and enter the following information:
  * Input type: text
  * Input text (hex): the 96-character key previously retrieved from the ** ZTOKEN ** column
  * Selectbox Plaintext / Hex: Hex
  * Function: AES
  * Mode: ECB
  * Key (hex): 000000000000000000000000000000000000
  * Selectbox Plaintext / Hex: Hex
  * Click on the `Decrypt` button. Your token are the first two lines on the right block. These two lines should contain your 32 character token.

### 4th method (Android)
* Allow unknown sources:
 Installing apps outside the Google Play Store requires changing phone settings to allow installation of apps from so-called "unknown" sources.
 On his phone: Settings ? General tab ? Security then check Unknown sources.
* Install the modified mid-home app:
 We are going to install a modified version of mi home which clearly displays its token directly in the app. Simple and efficient.
 Download the modified mihome app on your android phone: (07/12/18 5.4.37)

 https://drive.google.com/drive/folders/18OyC78peggCdiMmmT7i5bpvpdMJl1Ec1?usp=sharing
 
* Install it, open it and log in with your Xiaomi ID to recover its usual configuration.
* Recover your token:
 On the new Mi Home app: Go to the appliance, configuration menu / general settings / network information
 Two lines interest us: the local IP address of the robot and the token
 Note this information carefully and without error. When it's good, you can uninstall modified Mi Home to reinstall the official version.
 
### 5th method (Packet Sender Tool)
During setup of Mi Home devices the device tokens can be retrieved by sending a ping command to the device. This method uses a tool called Packet Sender which you will need to download. Choose the portable version which does not require installation.
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


### Extraction from Mi Home logs (Android)

A simple method on Android is to install version 5.4.49 of Mi Home. The installation file is easy to find for example on apkmirror. The special feature of this version is to create a log file containing all of the device information.
Once installed, just open it and connect. At that time, you will already have a log file with all the info. It is located at this location: SmartHome / logs / plug_DeviceManager

## Configuration of WiFi equipment

This section deals with additional WiFi equipment. There is no question of Yeelight or the Aqara gateway.

* ** Xiaomi Mi Robot Vacuum **: online, status, battery, suction (force + slider, attention beyond 77, you go beyond turbo mode), surface cleaned, cleaning time, error status, suction power, start, stop, pause, return to base, spot function, "where are you?", refresh.
* ** Viomi Vacuum STYJ02YM **: online, status, battery, suction, mop mode, surface cleaned, cleaning time, error status, suction power, start, stop, pause, base return, Map ID, define Map, room mode , refresh.
* ** Xiaomi Smart Mi Air Purifier (including Pro or V2 with screen) **: status, air quality, humidity, temperature, filter, speed, buzzer (on / off), led (action on it too), start / stop (with the different modes available).
* ** Xiaomi Smart Ultrasonic Humidifier **: status, mode, humidity, target humidity (+ set slider), temperature, buzzer (status + activation), led (status + activation), start / stop (with the different modes available ).
* ** Xiaomi Smart Air Quality Monitor PM2.5 Detector **: air quality, battery, refresh.
* ** Xiaomi Mi Power Strip Wifi **: on, off, status, temperature, Intensity, power, refresh.
* ** Xiaomi Mi Power Plug Wifi **: on, off, status, use, voltage, charge voltage, charge power, power consumed, refresh.
* ** Xiaomi Philips Eyecare Smart Lamp **: status, on / off, brightness (+ slider), eyecare (status, scenes + different modes available).
* ** Xiaomi Philips Ceiling **: status, on / off, brightness (+ slider), white color (info + cmd), Auto CCT (status + cmd), scenes (status + activation scenes).
* ** Xiaomi Philips E27 (also works for E14, to be validated on spots) **: status, on / off, brightness (+ slider), white color (info + cmd), Auto CCT (status + cmd) , scenes (status + scene activation).
* ** Xiaomi Mi Electric Rice Cooker **: not implemented as is.
* ** Fan **: status, temperature, humidity, buzzer (status + activation), led (status + activation), start / stop (with the different modes available), speed and natural speed info, rotation (and commands for set it up, turn).

For the Viomi, the parts mode allows it to be requested to switch to a parts list.

First, you must make sure you are on the correct Map (an info command gives you the current map, an action command allows you to change it by providing the ID in the message)

Then, to launch the parts command, you have to put in the message for example: 0,1,1,17.

Which means :

* First digit: complete cleaning (0) or edges (1)

* Second digit: start (1) or pause (2)

* Third digit: the number of pieces to be made

* Fourth digit and following: IDs of parts (which start at 10, not 0)

Second example for 4 pieces: 0,1,4,11,12,13,14

To find IDs, test and try

Other information for the levels reported by Viomi:

     Water level (water_grade) => 11 = Low / 12 = Medium / 13: High
    
     Aspiration (fan_speed) => 0 = Silent / 1 = Standard / 2 = Medium / 3 = Turbo
    
     Mode (is_mop) => 0 = aspi / 2 = aspi and washing / 3 = washing
