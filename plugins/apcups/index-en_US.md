# APC inverters

## Presentation

This plugin makes it possible to recover information from APC inverters and also to be warned about their events.

It uses apcupsd as a dependency (installed during activation of the plugin) and allows you to manage an APC inverter via USB or remote.

The information provided is:

* Load: the% load of the inverter relative to its power
* Battery: the% charge of the UPS battery
* Incoming Current: the supply current voltage of the inverter
* Model: the inverter model
* Status: the status of the inverter
* Time on battery: the available autonomy time
* Battery voltage: battery voltage
* Event: any event detected by the apcupsd service which is transmitted by push to Jeedom

## Configuration

### General configuration

The plugin does not have a general configuration.

Note that when the plugin is activated, it performs two actions:

* Installation and configuration of apcupsd to manage a USB inverter
* Creation of equipment to declare the USB inverter created

### Equipment configuration

As indicated above, a first device is created upon activation. It is functional for a local USB inverter.

You can add other equipment if you have other inverters on the network for example.

The plugin can be found in the Monitoring category.

### Settings

The equipment has 3 parameters:

* Address: the connection address for obtaining APC information (127.0.0.1 by default)
* Port: the listening port of the apcupsd service (by default 3551)
* Power: the power of the inverter (necessary to gain access to consumption)

Attention: you must enter an ip address and not a name for the address, it is used to identify who is issuing a push event

For power, it is easily identified in the model name (Back-Up 550 USB for example, 550 is power)

### Use

The equipment has an associated widget for the dashboard.

Consumption is available to be integrated into the Energy plugin, for example via a calculation between the load and the power of the inverter.

The event information will be useful for triggering scenarios, as well as the status.

Battery life can be a good addition in scenarios triggered on status for example.

### Configuration of an inverter accessible via the network

#### Installation of apcupsd

Apcupsd must be installed of course, it will be he who will be questioned

It must therefore be installed via the appropriate method on your system

#### Listening address configuration

In the file /etc/apcupsd/apcupsd.conf, you must check the NISIP parameter so that it is the address of the machine on the network and not 127.0.0.1 (which would not be searchable)

NISIP 192.168.0.100

#### Modification of apccontrol to activate the push

In the / etc / apcupsd / apccontrol file, you must add at the beginning a line to call Jeedom on events.

Copy the one that is present on Jeedom

#### Configuration in Jeedom

Now, all you have to do is add a device and enter the address you filled in the configuration

### Events provided by apcupsd


Here is the list of events that apcupsd can send

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

> Does the plugin rely on third-party APIs?

The plugin uses apcupsd to retrieve its information.

## Troubleshooting

> I have no information going back

Equipment must be created and the information filled in.

## Changelog

[See dedicated page](changelog.md).
