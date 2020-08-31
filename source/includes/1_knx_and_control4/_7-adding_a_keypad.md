## Adding a Keypad

To add a KNX enabled Keypad to your project, you will need to add the knx\_keypad.c4i driver. You will need to add the knx\_keypad.c4i file to directory path for your other Lua based drivers.

This is typically: C:\Users\user\Documents\Control4\Drivers

Once added, you can open Composer Pro and find the driver under the Items area. Click on the Search tab and select Local Database. Using Device Type of “other” and the Manufacturer of “KNX” you will see the Keypad driver.


<img src="images/1_7-01.png"/>

Double click on the Keypad driver to add it to your project.

The Keypad driver can be configured for one to eight buttons. Each button can be mapped to a KNX button on a keypad. You are not restricted to mapping all of the buttons to the same keypad. Each button is mapped based on the addressed used in the Button Address parameter.

The Keypad driver allows you to capture KNX button press events that (through programming) can be used to control other devices in the Control4 project. 

The button mode is used to configure the button to match the corresponding KNX button configuration.

Through Control 4 programming they can also initiate Actions such as ramping up and down audio volume. For this reason it is important that you have the ability to configure your KNX Configuration and Group Address values for your keypad so it can accomplish everything that you want the keypad to do.

For example, the parameters for the keypad must be set to “Switching” in the ETS software and a Button Press must to be set to ON and Button Release set to OFF. Otherwise, Programming in Composer Pro will not work.

Clicking on the properties for the Keypad will display the following screen:

<img src="images/1_7-02.png"/>

The example above shows the configured properties for an eight button keypad utilizing eight button configurations. Button configurations are designated by a number (Button 5) and have a one-to-one relationship with a physical button on keypad. Currently, eight is the maximum amount of buttons supported. Each of the buttons on a keypad can have up to three configurable fields. These include: Button Mode, Button Address and Button Value.

**Button Mode** – The drop down box allows for the selection of several button press configurations. Two important factors should be considered when selecting a button mode:
 
1. How you plan on using Control4 programming in conjunction with button press and/or button click events.
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