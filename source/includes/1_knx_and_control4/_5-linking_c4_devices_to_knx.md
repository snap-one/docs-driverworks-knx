## Linking C4 Devices to KNX Device Object Functions

In order to configure KNX devices with Control 4, you will need to obtain a list of the device’s Object Function and their Group Addresses. This list can either come from your KNX dealer, EIB Installer or through the use of an approved Engineering Tool Software (ETS) software/database program that is compatible with the KNX standard. 

Each of the Control4 devices in your project will need to be linked to the KNX Device Object Functions that are available for that device. This is accomplished through the Properties page in Composer Pro. For purposes of example, we will use the switch driver to assign a Function Group Address.  

Begin by adding the KNX Switch driver to your project. You will need to add the knx\_switch.c4i file to directory path for your other Lua based drivers.

This is typically: C:\Users\user\Documents\Control4\Drivers

Once added, you can open Composer Pro and find the driver under the Items area. Click on the Search tab and select Local Database. Using Device Type of “Light” and the Manufacturer of “KNX” you will see the switch and dimmer drivers.

<img src="images/1_5-01.png"/>

Double click on the Switch driver to add it to your project. Clicking on the properties for the switch device will display the following screen:

<img src="images/1_5-02.png"/>

It is important to understand that each property for a driver needs to be linked to a KNX Device’s Object Function. The value that is used here is the KNX Object Function Group Address. In our example, our switch supports two object functions: ON/OFF switching object and Feedback (Status) ON/Off.

To link the ON/OFF switching functionality to this device, it is necessary to enter the KNX Device’s Switching Object Function Group Address. This is a unique value that is configured in your KNX protocol.  Based on our example KNX project, the current configuration for this is a value of 0/0/10. By entering this value in the Set Address field, our switch now has the ability to turn a device ON and OFF.

The switch driver also supports the Feedback (Status Address.) This is a value that, when enabled, allows for the switch to communicate its state over the KNX Network. Once again, this is a unique value to your KNX configuration. Based on our example KNX project, the current configuration for this is a value of 0/0/11. By entering this value, our switch will be able to get feedback from the network which can be displayed on touchscreen and other devices.

**An Important Note about Status Address Settings**
In some instances, the Feedback functionality may not be added to the list of available Object Function Group Addresses for a device. It is important to validate that Feedback is added through an ETS program or your KNX Dealer. If Feedback is not included as a function it will be difficult to monitor/troubleshoot your KNX device configuration. Control4 recommends Feedback being added and enabled for all devices. 

The remainder of this document will outline the steps required to add a KNX supported dimmer and keypad to your project. As you add KNX devices to your project you will need to know beforehand the Object Function and Group Address Values that are associated with the device. These values represent commands or notifications that are supported under the KNX architecture for the device. It is not recommended to proceed with the implementation unless these values are obtained.


