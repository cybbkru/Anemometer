# Anemometer
In my home ventilation unit this Anemometer helps to clear filters in time ( before air flow becomes too low). 

Hall-sensor and magnet are used to generate impulses according to rotation rate of Anemometer.

The "Sonoff basic" esp8266 wifi-relay flashed with Tasmota firmware used to count sesnsor impulses. (In my vent. unit it also enables/disables fan.)
You can use ANY ESP8266 based device (cheapest ESP-01 for example) having 1 free pin.

To count impulses attach Counter1 to RX pin of module (GPIO2 and GPIO14 are also available in some untits, you can try another available pin):
!["Tasmota modue settings.png"](https://github.com/cybbkru/Anemometer/blob/main/Tasmota%20modue%20settings.png)



To publish counted impulses every 10 seconds to  MQTT topic "wind/vent1" use commands in Tasmota console:
```
Teleperiod 10
rule1 on tele-counter#c1>-1 do publish wind/vent1 %value% endon on tele-counter#c1>0 do counter1 0 endon
rule1 1
```

# Restrictions
Indoor use only.

# TODO
1. Draw printable bottom cover with cable gland.
2. Redraw design for outdoor use (enlarge clearances and parts overlays to prevent raindrops infiltration).
