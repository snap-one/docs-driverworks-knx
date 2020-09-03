## Adding a Keypad

Open Composer Pro and find the driver under the Items area. Click on the Search tab and select Online. Search for "KNX Keypad" using Manufacturer of “KNX” and you will see the Keypad driver.

<img src="images/1_7-01.png"/>

Double click on the Keypad driver to add it to your project.

The Keypad driver can be configured for one to ten buttons. Each button can be mapped to a KNX button on a keypad. You are not restricted to mapping all of the buttons to the same keypad. Each button is mapped based on the addressed used in the Button Address parameter.

The Keypad driver allows you to capture KNX button press events that (through programming and connections) can be used to control other devices in the Control4 project.

The button mode is used to configure the button to match the corresponding KNX button configuration.

Through Control4 programming and connections they can also initiate Actions such as ramping up and down audio volume or lighting scenes. For this reason it is important that you have the ability to configure your KNX Configuration and Group Address values for your keypad so it can accomplish everything that you want the keypad to do.

For example, for "Press/Release (On/Off)" button mode, the parameters for the keypad must be set to “Switching” in the ETS software and a Button Press must be set to ON and Button Release set to OFF. Otherwise, Programming and control connections in Composer Pro will not work.

Clicking on the properties for the Keypad will display the following screen:

<img src="images/1_7-02.png"/>

The example above shows the configured properties for an eight button keypad utilizing eight button configurations. Currently, ten is the maximum amount of buttons supported. Each of the buttons on a keypad can have the following fields: Button Name, Button Mode, Button Address and Button Value.

**Button Name** - Name or short description of the button. This field will be used for the name of the control connections, therefore it is recommended to set it to a meaningfull value.

**Button Mode** – The drop down box allows for the selection of several button press configurations. Two important factors should be considered when selecting a button mode:
 
1. How you plan on using Control4 programming and connections in conjunction with button press and/or button click events.
2. The configuration for the buttons on your KNX enabled Keypad.

The following modes are provided if you wish to create programming based on Button Press and Release events:

**Press/Release (On/Off)** – This mode is selected when a button press sends a value of 1 from KNX and a value of 0 is sent from KNX upon release.

**Press/Release (Off/On)** – This mode is selected when a button press sends a value of 0 from KNX and a value of 1 is sent from KNX upon release.

The following table outlines the Mode to use based on the value received from KNX:

| Mode | Sent Upon Press | Sent Upon Release |
| --- | --- |  --- |
| On/Off | 1 | 0 |
| Off/On | 0 | 1 |

**The following modes are provided if you wish to create programming based on Button Click events:**

**Click: On** – The click event is fired when a value of 1 is received from KNX.

**Click: Off** - The click event is fired when a value of 0 is received from KNX.

**Toggle** – The click event is fired when any value is received from KNX.

**Value (1 byte)** – The click event is fired when the defined is received from KNX

| Mode | 0 | 1 | Defined Value |
| --- | --- |  --- | --- |
| Click: On |  | X |  |
| Click: Off | X |  |  |
| Toggle | X | X |  |
| Value (1 Byte ) |  |  | X |

### Control bindings

KNX Keypad driver has available BUTTON\_LINK, RELAY and CONTACT\_SENSOR connections for each button as way of controlling other devices in the Control4 system. These connections are dynamically created depending on the number of buttons and their modes.

As an example, we will use a KNX button to toggle a ligthing scene using the BUTTON\_LINK connection. KNX button is configured to send On (1) value on press and Off (0) value on release. Corresponding button mode in the driver for this configuration is "Press/Release (On/Off)".

<img src="images/1_7-03.png"/>

After configuring the button 1 in the Properties page, navigate to Connections page and click on the KNX Keypad device. BUTTON\_LINK connection will become available for this button. Connect it to a Toggle Button Link of a lighting scene. Now, every time a customer holds the button, the scene will ramp in the opposite direction.

<img src="images/1_7-04.png"/>
