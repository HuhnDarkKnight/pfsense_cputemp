# pfSense RRD CPUTemp

This is a simple implementation of a RRD Graph for the CPU Core temperatures.

It is written for a quad-core CPU, so you need to change it to fit your system.

As it uses sysctl to get the temperatures, make sure your sensors are supported and enabled (System > Advanced > Miscellaneous > Thermal Sensors).


pfSense version: 2.2.6-RELEASE

Based on [https://forum.pfsense.org/index.php?topic=42388.0](https://forum.pfsense.org/index.php?topic=42388.0)

## Sensors

To see all sensors use

	# sysctl dev.cpu | grep temperature
	
This will give you a list of all CPU temperature sensors.

If your sensor number is not 4 you need to change the files after the patch to match the number (See TODO in files).

## Installation


	# cd /
	# patch -p0 -u < /path/to/coretemp.patch
	
If you need to change some sensors edit

	etc/inc/rrd.inc
	usr/local/www/status_rrd_graph_img.php
	
and look for TODOs.
	
Then reload the webConfigurator (option 11 in console main menu).

You should now get a new RRD Graph under System. It may take up to 1 minute to show actual values.

