# Yeelight Wifi

## Lamp configuration

A full presentation of the range is available here: [Presentation article in French] (https://lunarok-domotique.com/plugins-jeedom/xiaomi-home-jeedom/yeelight-xiaomi-wifi-lamp/).

In the Yeelight application, you must activate the ** control option ** on the local network. You have to activate this switch in the options of each bulb / strip. In addition, the equipment must be on the same network as Jeedom.

## Creation of equipment

A ** scan ** button allows you to automatically create all the equipment corresponding to the Yeelight protocol available on the network (only those that do not already exist in Jeedom, of course).

## Commands for compatible equipment

Compatible lamps offer the following commands by default: ** Switch on **, ** Switch off **, ** toggle **, ** brightness **, ** sequence **.

Some lamps have more commands:

* ** Yeelight White **: no other orders.
* ** Desklamp **: white temperature.
* ** Yeelight RGB **: Online, Status, Define RGB color, Moonlight, Sunlight, Programmed switch-off, Chain stop, Brightness information, White temperature, White temperature information, Mode, Define HSV color, HSV Color, Define HSV Saturation, HSV Saturation, RGB Color, Refresh.
* ** RGB banner **: Online, Refresh, Status, Define RGB color, Moonlight, Sunlight, Programmed extinction, White temperature, Stop chaining, Brightness information, Mode, Define HSV color, HSV color, Define HSV saturation, HSV saturation, RGB color.
* ** Bedside lamp ** (golden base): RGB color, white temperature, day mode, night mode, HSV colors.
* ** Yeelight Ceiling **: white temperature, day mode, night mode.
* ** Yeelight Ceiling 450 and 480 **: white temperature, day mode, night mode.
* ** Yeelight Ceiling 650 **: white temperature, day mode, night mode, RGB colors.

### The sequence command

A special order ** sequence ** is created. It is intended to be used in a scenario only, because we must send specific content to the order.
Here is a commented example of this command:

> ** `3 recover rgb, 255,0,0,500,100-wait, 400-rgb, 255,255,0,500,100` **

* ** `3` **: Defines the number of times that the sequence of effects must be applied before stopping (0 means unlimited).
* ** `recover` **: one of the 3 possible options for the end of the chain (` recover` = returns to the state preceding the chain, `off` = goes out,` stay` = stays at status of the end of the sequence)
* the third element is the continuation of the states with their transition, there are 4 possible (attention: it is not necessary to put space):
  * ** `hsv` **: parameters (hue, saturation, duration = 300, brightness = 100).
  * ** `rgb` **: parameters (red, green, blue, duration = 300, brightness = 100).
  * ** `temp` **: parameters (degrees, duration = 300, brightness = 100).
  * ** `wait` **: parameter (duration = 300).

The numbers given for ** duration ** or ** brightness ** are the maximum allowed.

You must enter the sequence with `-` between each effect. For each, there must be their name and all parameters separated by commas.
