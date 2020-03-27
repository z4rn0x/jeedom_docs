# Xiaomi Home

## Introduction

A full presentation of the plugin is available on this article : [Article de présentation, in french](https://lunarok-domotique.com/plugins-jeedom/xiaomi-home/).

The plugin implements 3 Xiaomi protocols, which gives a substantial range of supported hardware:

### **The Xiaomi Aqara zigbee protocol**
The Xiaomi Mi Home Gateway (also called Xiaomi gateway) allows you to use different Zigbee sensors from Xiaomi. See doc Aqara. [See doc Aqara](aqara.md).
Please note, the Aqara Homekit gateway is different and does not have the API allowing connection to home automation. In addition, this new gateway only allows the use of new sensors, usually stamped "Aqara" (square / rectangular shapes)

### **Lights Yeelight**

Lamps that support the Yeelight Wifi protocol. See the Yeelight doc. [See doc Yeelight](yeelight.md).

### **Wifi Appliances**

There is also a Xiaomi protocol common to many WiFi devices. This protocol is implemented in the plugin and makes compatible the appliances using it. See the Wifi Appliances doc. [See doc Wifi Appliances](wifi.md).

> What about Bluetooth devices?
>
> Xiaomi Bluetooth products are not supported by this plugin. However, the BLEA (Bluetooth Advertisement) plugin available on the Jeedom market manages a good part of it, including:
>
> * Miband bracelets (at least for the presence on the 2),
> * bedside lamp (1st generation, gray base),
> * balance (1st generation with weight only).

## FAQ

> What type of Xiaomi gateway is supported?

The "Aqara" with led ring for the Zigbee. It must be set in developer mode to access it locally. For this, you need firmware at least 1.4.

> I can't switch my Aqara gateway to local mode?

You must also use the Mi Home smartphone app in English and set to China Mainland if you encounter inclusion problems.

> Information from my sensors does not go up?

If you do not have an equivalent order created in Jeedom, the API may not expose this information. You may have to wait for a firmware update. All the information does not go back to the same frequency, for example the battery can be sent only daily.

> I can't control my Aqara sensors (color and its gateway, socket ...)?

You must enter the gateway key, visible in Mi Home, on the gateway equipment in Jeedom.

> My orders on Aqara sensors which worked before, do not work any more?

Check if the key has changed in Mi Home, this can happen after a firmware update for example.

> Jeedom can't find the gateway and the sensors?

Check that your router allows broadcast packets from the Wifi network to pass through Ethernet, for example.

> My Jeedom is installed on Docker and does not see the gateway?

The gateway communicates in broadcast, so you must be on the same network (host mode) and make sure that the Broadcast packets are received on Jeedom.

> Jeedom does not see the new Gateway stamped "Aqara Homekit"?

It does not offer the Aqara API, it does not work with the plugin, you have to take the model presented in the doc. In addition, the Homekit gateway is not compatible with all of the Xiaomi sensor models.

> Jeedom can't see my gateway?

She must go back alone in Jeedom. If it is not the case, it is possible to check if it is correctly parameterized with the command:

nmap -p 9898 -sU ip.ga.te.way

> How many sensors can there be on a Gateway Aqara?

User feedback indicates 31 sensors + the Gateway. Beyond that, you must remove the pairing of a sensor to replace one. The plugin supports several Gateways.

> What bulbs are supported by this plugin?

Yeelight Wifi only (the list is provided in the documentation).

> Some Yeelight bulbs do not go up in Jeedom?

The Yeelight Wifi bulbs must all be configured with the developer mode to be reachable on the local network. For this, you need to install the Yeelight application (and not just Mi Home), enter your username / password, go to each device, access the parameters via the '...' and activate the 'Developer Mode' . Note: It is not necessary to change the language of the application.

> I can't control an appliance, like the robot, for example?

Check that you have obtained the token, for the appliances which do not provide it, tutorials are present in the doc (wifi.md).

## Changelog

[See dedicated link](changelog-en_US.md).
