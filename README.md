# MatterThermostat

This code base is based upon the Espressif Arduino IDE Matter example code for a simulated thermostat (https://github.com/espressif/arduino-esp32/blob/master/libraries/Matter/examples/MatterThermostat/MatterThermostat.ino). This code base was modified to display and perform temperature arithmetic using Fahrenheit instead of Celsius. Another addition was the introduction of the use of the DHT11 Temperature and Humidity sensor for the initial setting of the thermostat. 

This was all tested using Arduino's IDE (https://www.arduino.cc/en/software) where the serial monitor was used as well as uploading the code to the ESP32 microcontroller for testing with Home Assistant. 

# Joshua Suizo's Testing Environment:

# Home Assistant
Home Assistant was intialized using Oracle's VirtualBox VM machines using Home Assistant OS's .vdi file (https://www.home-assistant.io/installation/windows). From here, the OS will install itself into the virtual machine. Upon completion, the Home Assistant client becomes available for use at the localhost URL http://homeassistant.local:8123/. Within Home Assistant, there is an integration built in for Matter where it allows Home Assistant to act as a Matter Controller. This is also how the thermostat was able to be commissioned and controlled. 

# Arduino IDE
The Arduino IDE supports development of Espressif's ESP32 and all ESP32 variant boards. This is done by navigating to Preferences and including the following GitHub link in the field "Additional Boards Manager URLs": https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json. 
![ESP32 Board Manager URL](https://github.com/user-attachments/assets/2c1d577e-f680-4193-b7ea-ad8f705968b7)

In the Tools tab, navigate to 
Tools > Boards > Board Manager and then search for the esp32 package by Espressif 
![Board Manager Finder in Tools](https://github.com/user-attachments/assets/eebbe71d-acea-4220-925e-33e30e9b9308)
![esp32 by espressif systems in Board Manager](https://github.com/user-attachments/assets/87579891-ec9b-434d-a872-9ec4266c34a5)


This gives you the ability to use ESP32 variant boards within the IDE. For using the DHT11 Sensor, additional libraries are required. This can be amended by navigating to 
Sketch > Include Library > Manage Library and searching for "DHT sensor library" by Adafruit as well installing the dependency "Adafruit Unified Sensor" also by Adafruit. 

![DHT11 Sensor Library in Library Manager](https://github.com/user-attachments/assets/c50f9e8b-0daf-43d0-b248-5c3e475d11ff)![Install All Dependencies](https://github.com/user-attachments/assets/2ba62dc7-79bf-4b77-a31f-a0de1d180b16)
![Installation Complete](https://github.com/user-attachments/assets/d6c5c6c3-4a17-49ff-8257-1c047905d171)

Both of these libraries are necessary for the use of the DHT sensor within the code base. 

The board might require additional drivers like the Silicon Labs CP210x USB to UART Bridge VCP Drivers (https://www.silabs.com/developer-tools/usb-to-uart-bridge-vcp-drivers). 
After these drivers are installed, then we change the board to one connected to the COM port and change the board type to "ESP32 Dev Module". Within the Tools section, we tweak the settings of the board to accommodate the large size of the application

![Board Settings](https://github.com/user-attachments/assets/701093bc-6e3b-4b0d-8492-a9d5ec403de8)

Here, we changed the Partition Scheme of the board to be "Large APP (3MB No OTA/1MB SPIFFS)" to accommodate for the application size. After copying the code and intializing the "ssid" and "password" variables for the desired network, we go ahead and upload the code to the ESP32. From there, we enable the Serial Monitor to view any debugging and print to serials by the code. 
