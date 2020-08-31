## KNX Support Overview

Control4 supports integration with devices using the standardized KNX control network topology. Note that the scope of support of this integration only includes products labeled with the KNX trademark. These devices have been tested for KNX protocol support as well as correct data coding by accredited third party test labs using the KNX standardized Data types.
The KNX protocol supports a wide variety of home automation applications including:

- Lighting control
- Heating/ventilation & Air Conditioning control
- Shutter/Blind & Shading control
- Alarm Monitoring
- Energy Management & Electricity/Gas/Water metering
- Audio & video distribution

Through the Online Driver Database, Control4 has made available four drivers to assist with KNX implementation into a Control4 project. These include:

- Switch Driver:  knx\_switch.c4i
- Dimmer Driver:  knx\_dimmer.c4i
- Keypad Driver:  knx\_keypad.c4i
- Generic Driver: knx\_generic.c4i
- Network Driver: knx\_network.c4i

In addition to these, a KNX Network driver is also available in the Online Driver Database. It is named: knx\_network.c4i. 
The network driver in conjunction with any/all of the device drivers listed above will allow you to use the KNX protocol to control keypads, dimmers and switches within the Control4 environment.
