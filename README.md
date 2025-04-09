# MatterThermostat

This code base is based upon the Espressif Arduino IDE Matter example code for a simulated thermostat (https://github.com/SiliconLabs/arduino/blob/main/libraries/Matter/examples/matter_thermostat/matter_thermostat.ino). This code base was modified to display and perform temperature arithmetic using Fahrenheit instead of Celsius. Another addition was the introduction of the use of the DHT11 Temperature and Humidity sensor for the initial setting of the thermostat. 

This was all tested using Arduino's IDE (https://www.arduino.cc/en/software) where the serial monitor was used as well as uploading the code to the ESP32 microcontroller for testing with Home Assistant. 

#Joshua Suizo's Testing Environment:

#Home Assistant
Home Assistant was intialized using Oracle's VirtualBox VM machines using Home Assistant OS's .vdi file (https://www.home-assistant.io/installation/windows). From here, the OS will install itself into the virtual machine. Upon completion, the Home Assistant client becomes available for use at the localhost location http://homeassistant.local:8123/. Within Home Assistant, there is an integration built in for Matter where it allows Home Assistant to act as a Matter Controller. This is also how the thermostat was able to be commissioned and controlled. 

#Arduino IDE
The Arduino IDE supports development of Espressif's ESP32 and all ESP32 variant boards. This is done by navigating to Preferences and including the following GitHub link in the field "Additional Boards Manager URLs": https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json. In the Tools tab, navigate to Tools > Boards > Board Manager and then search for the esp32 package by Espressif; this gives you the ability to use ESP32 variant boards within the IDE. For using the DHT11 Sensor, additional libraries are required. This can be amended by navigating to Sketch > Include Library > Manage Library and searching for "DHT sensor library" by Adafruit as well as "Adafruit Unified Sensor" also by Adafruit. Both of these libraries are necessary for the use of the DHT sensor within the code base. 
