# Asuswrt router

## Presentation

This plugin allows you to retrieve connection information from devices on an Asuswrt router.

It uses the SSH connection to the Asus router to retrieve the WAN speed and information from the devices present.

## Configuration

### General configuration

The plugin requires entering 3 parameters:

* IP address of the router
* SSH user (normally admin)
* Password (same as via conf per web page)
* (Optional) List of AP in AIMesh, it must be the IP separated by a;

You must activate access to SSH by the local address.

### Equipment configuration

It is possible by equipment to select a plugin in which it is present, the equipment of the plugin will then be activated / deactivated automatically according to its presence on the router.

The only plugins supported are: Xiaomi Home, Shelly and Hikvision

### Settings

The equipment has several controls:

* MAC address
* IP adress
* Hostname
* Connection used (ethernet or wifi)
* RSSI (equal to 0 if absent or ethernet)
* Connection status in text
* Presence (binary)
* Internet access status
* Prohibit Internet access
* Allow internet access
* Wake On Lan

## FAQ

> Does the plugin rely on third-party APIs?

The plugin uses a local SSH connection to retrieve its information.

> I have equipment on my fixed IP network, the hostname is not seen by the plugin / router, how do I do this?

You must fill in the file /jffs/configs/dnsmasq.conf.add on your router.

## Changelog

[See the dedicated page] (changelog.md).
