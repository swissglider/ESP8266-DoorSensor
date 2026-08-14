> [!IMPORTANT]
> **Archived / Nicht mehr gepflegt**
>
> This project is no longer maintained. I no longer own the required hardware and therefore cannot provide support or continue development. The repository remains available as a reference. You are welcome to fork it and continue development independently.
>
> Dieses Projekt wird nicht mehr weiterentwickelt. Die benötigte Hardware ist nicht mehr vorhanden; deshalb kann ich keinen Support leisten. Das Repository bleibt als Referenz verfügbar. Forks und eine eigenständige Weiterentwicklung sind ausdrücklich willkommen.

# ESP8266-DoorSensor

This is a simple Door/Windows open/close sensor (Reedsensor) with a temperature/humity sensor (DHT22) and a display (SSD1306) that shows the Temperature and the Humity.

The os in the esp8266 is Tasmota.


## Schema
![Image of Fritzing](https://github.com/swissglider/ESP8266-DoorSensor/blob/master/fritzing/ESP8266-DoorSensor1.png?raw=true)

## Configuration on Tasmota:
![Image of Tasmota](https://github.com/swissglider/ESP8266-DoorSensor/blob/master/picture/Office-Door_Configuration.png?raw=true)

## Set OLED Display for SSD1306 on tasmota on the console
Check if Display available:
```
CMD: I2Cscan
MQT: stat/door_office/RESULT = {"I2CScan":"Device(s) found at 0x3c"}
```
Check if DisplayAddress is 60 if not set it:
```
CMD: DisplayAddress
MQT: stat/door_office/RESULT = {"DisplayAddress1":60}

CMD: DisplayAddress 60
MQT: stat/door_office/RESULT = {"DisplayAddress1":60}
```
Check DisplayMode is 0 if not set it:
```
CMD: DisplayMode
MQT: stat/door_office/RESULT = {"DisplayMode":1}

CMD: DisplayMode 0
MQT: stat/door_office/RESULT = {"DisplayMode":0}
```
Check if DisplayDimmer is 100(15) if not set it:
```
CMD: DisplayDimmer
MQT: stat/door_office/RESULT = {"DisplayDimmer":1}

CMD: DisplayDimmer 100
MQT: stat/door_office/RESULT = {"DisplayDimmer":15}
```
Check if Display is working:
```
DisplayText [s1l1c1]Hello how are you?
```
Clean Display:
```
DisplayText [z]
```
Display Power on/off:
```
Power ON
Power OFF
```
## Configure the Switch (Reed Sensor)
```
CMD: SwitchMode2 1
MQT: stat/door_office/RESULT = {"SwitchMode2":1}

CMD: SwitchTopic 1
MQT: stat/door_office/RESULT = {"SwitchTopic":"door_office"}
```
## Adaption on iobroker
- Change DisplayText to String (Zahl zu Zeichenkette)