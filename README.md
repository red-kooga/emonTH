# emonTH - Wireless Temperature and Humidity monitoring node 

Part of the openenergymonitor.org project

Main emonTH page: http://openenergymonitor.org/emon/modules/emonTH

Technical Hardware Wiki: http://wiki.openenergymonitor.org/index.php?title=EmonTH 

Schematic + CAD: http://solderpad.com/git/openenergymon/emonth

Design & related Blog posts: 
http://openenergymonitor.blogspot.com/2013/06/emonth-prototype.html
http://openenergymonitor.blogspot.com/2013/10/emonth-update-hardware.html
http://openenergymonitor.blogspot.com/2013/10/emonth-update-software-power.html
http://openenergymonitor.blogspot.com/2013/10/aa-battery-considerations.html
http://openenergymonitor.blogspot.com/2013/11/hardware-manufacture-begins-part-1.html
http://openenergymonitor.blogspot.com/2014/01/emonth-multiple-ds18b20-sensors.html

Builds on JeeLabs, Adafruit and Miles Burton 

## Libraries Needed
* RFu_JeeLib: https://github.com/openenergymonitor/RFu_jeelib
* Temperature control library: http://download.milesburton.com/Arduino/MaximTemperature/ (version 372 works with Arduino 1.0) and OneWire library: http://www.pjrc.com/teensy/td_libs_OneWire.html
* DHT22 Sensor Library  https://github.com/adafruit/DHT-sensor-library - be sure to rename the sketch folder to remove the '-'


## emonTH Firmwarwe
* **emonTH_DHT22_DS18B20** - Main emonTH temperature and humidity sensing firmware. Searches for either DHT22 or DS18B20 and reads temperature and humidity once per min (by default) and tx's data back to the emonBase via RFM12B. If both sensors are detected temperature will be sensed from DS18B20 and humidity from DHT22 

* **emonTH_DHT22_dual_DS18B20** - Derived from the main emonTH firmware, but capable of monitoring two (or more) DS18B20 external sensors. You'll need to discover your sensors' addresses to make use of this script - discover them with 'emonTH temperature search' utility sketch in 'Simple emonTH Sensor Test' folder

* **emonTH_DHT22_multiple_DS18B20** - Derived from the dual sensor emonTH firmware by Marshall Scholz. Capable of automatically discovering and monitoring up to 70 connected DS18B20 sensors. The downfalls of this version are that it uses slightly more power that\n the other sketches, and that the sensor order will probably change if an extra sensor is added once the node has been set up. (This can be easily rectified by changing the input logging feed in emonCMS)

* **emonTH_gas_reflection_analogue** - Enables the emonTH as a gas meter node using a phototransistor (or other pulse calculated from analogue input). Note that you will need to experiment to get the best position for your sensing apparatus (recommend an IR LED and matched phototransistor) and configure the sketch accordingly. Average and lowest readings are reported as extra inputs to help with calibration through emonCMS. While power requirements are significantly higher than for temperature monitoring (or interrupt-based pulse monitoring) these should still be respectable; tests are ongoing to determine battery life.

* **Simple emonTH Sensor Test** - 
	* emonTH DHT22 Test - 
	* emonTH DS18B20 Test
	* emonTH temperature search - utility sketch for finding hardware addresses of one or more DS18B20 sensors connected to emonTH one-wire bus
	* note; it may be more helpful to use the tester example code in the dallas onewire library for testing multiple onewire sensors.


**Note:**
* Default RFM12B settings: 433Mhz, network: 210, Node: 19 
* Readings are converted to integer when sent over RF multiple by 0.1 in emoncms to restore reading

# License
The emonTH hardware designs (schematics and CAD files hosted on http://solderpad.com/openenergymon) are licensed under a Creative Commons Attribution-ShareAlike 3.0 Unported License.

The emonTH firmware is released under the GNU GPL V3 license

The documentation is subject to GNU Free Documentation License 

The emonTH hardware designs follow the terms of the OSHW (Open-source hardware) Statement of Principles 1.0.






 
