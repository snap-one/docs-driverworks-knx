# KNX Support Overview

Control4 supports integration with devices through standardized KNX control network topology. Note that the scope of support of this integration only includes products labeled with the KNX trademark. These devices have been tested for KNX protocol support as well as correct data coding by accredited third party test labs using KNX standardized Data types.
The KNX protocol supports a wide variety of home automation applications including:

- Lighting control
- Heating/ventilation & Air Conditioning control
- Shutter/Blind & Shading control
- Alarm Monitoring
- Energy Management & Electricity/Gas/Water metering
- Audio & video distribution

Through the Online Driver Database, Control4 has made available following drivers to assist with KNX implementation into a Control4 project:

| Name  | Driver | Description |
| --- | --- | --- |
| KNX Switch | knx\_switch.c4i | Control of a KNX switch |
| KNX Dimmer | knx\_dimmer.c4i | Control of a KNX dimmer |
| KNX Keypad | knx\_keypad.c4i | Control of a KNX keypad |
| KNX Generic | knx\_generic.c4i | Control manufacturer or device specific functions not covered by the corresponding KNX device driver |
| KNX Blinds (2.9+) | knx\_blind.c4z | Control of a KNX blind or louver actuator |
| KNX Contact/Relay | knx\_contact\_relay.c4i | Control of up to 10 KNX relays and binary inputs |
| KNX Motion Sensor | knx\_movement\_sensor.c4z | Allows to add KNX a motion or presence sensor to Control4 project |
| KNX Single Setpoint Thermostat | knx\_thermostat.c4z | Control of a KNX single-setpoint thermostat. |
| KNX Heat or Cool Thermostat | knx\_heat\_or\_cool\_thermostat.c4z | Used in a 'seasonal changeover' systems. It is designed to drive two separate systems, one for heating and one for cooling, which are not active at the same time. |
| KNX Universal Thermostat | knx\_universal\_thermostat.c4z | Contains a database of 21 thermostat models. The driver adjusts its configuration and operation based on the selected model. |
| Control4 KNX Thermostat | control4\_knx\_thermostat.c4z | Driver for Control4 KNX Thermostats: C4-KNX-THERM-xx, C4-KNX-BCET1-2-xx, C4-KNX-BCET3-6-xx, C4-KNX-BCET5-10-xx products |
| Control4 Split Unit Gateway | control4\_knx\_split\_unit\_gateway.c4z | Driver for C4-KNX-SUAC product |

In addition to these, drivers for communication with the KNX system are also available in the Online Driver Database:

- KNX Routing Gateway: knx\_routing\_gateway.c4z (Recommended)
- KNX Network: knx\_network.c4i

These network drivers in conjunction with any/all of the device drivers listed above will allow you to use the KNX protocol to control keypads, dimmers and switches within the Control4 environment.

Control4 recommends the usage of the KNX Routing Gateway driver. This driver uses the KNXnet/IP Tunneling protocol which, due to its strict timing requirements for the Control4 system, causes occasional disconnection between Control4 and the KNX system. KNX Routing Gateway driver eliminates this issue by using the KNXnet/IP Routing connection-less multicast protocol, which is more robust compared to the Tunneling protocol.
