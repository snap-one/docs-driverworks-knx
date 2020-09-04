## Linking C4 Devices to KNX Device Group Objects

In order to configure KNX devices with Control4, you will need to obtain a list of the device’s Group Objects and their Group Addresses. This list can either come from your KNX dealer, EIB Installer or through the use of an approved Engineering Tool Software (ETS) software/database program that is compatible with the KNX standard.

Each of the Control4 devices in your project will need to be linked to the KNX Group Objects that are available for that device. This is accomplished through the Properties page in Composer Pro. For purposes of example, we will use the switch driver to assign a Function Group Address.

Begin by adding the KNX Switch driver to your project. Open Composer Pro and find the driver under the Items area. Click on the Search tab and select Online. Using Type of “Light (v2)” and the Manufacturer of “KNX” you will see the switch and dimmer drivers.

<img src="images/1_5-01.png"/>

Double click on the Switch driver to add it to your project. Clicking on the properties for the switch device will display the following screen:

<img src="images/1_5-02.png"/>

It is important to understand that each "Address" property for a driver needs to be linked to a KNX Device’s Group Object Function. The value that is used here is the Group Address associated with the Group Object. In our example, our switch supports two functions: switching (ON/OFF) and switching feedback (ON/OFF status) objects.

To link the ON/OFF switching functionality to this device, it is necessary to enter the KNX Device’s Switching Object Group Address. This is a unique value that is configured in your KNX configuration. Based on our example KNX project, the current configuration for this is a value of 0/0/10. By entering this value in the Set Address field, our switch now has the ability to turn a device ON and OFF.

The switch driver also supports the Feedback (Status Address). This is a function that, when enabled, allows for the switch to communicate its state over the KNX network. Once again, this is a unique value to your KNX configuration. Based on our example KNX project, the current configuration for this is a value of 0/0/11. By entering this value, our switch will be able to get feedback from the KNX system which can be displayed on touchscreen and other devices.

**An Important Note about Status Address Settings**
For some KNX devices, the Feedback functionality may not be enabled by default. It is important to validate that Feedback is enabled and that a Group Address is linked with the Feedback Group Object through the ETS tool or your KNX Installer. If Feedback is not enabled, it will be difficult to monitor/troubleshoot your KNX device configuration. Control4 recommends Feedback being added and enabled for all devices.

In addition to enabling the feedback functionality, it is recommended to set the "Read" flag (R) for all status Group Objects that are used by the Control4 drivers. The KNX Routing Gateway driver will issue read requests for all status addresses found in the project at startup. A read request will only work if a corresponding Group Object has its Read flag set in the ETS. The Read flag enables the object value to be read out i.e. a response telegram is only sent after a read telegram if the read flag of the object has been set.

The remainder of this document will outline the steps required to add a KNX supported dimmer and keypad to your project. As you add KNX devices to your project you will need to know beforehand the Object Function and Group Address Values that are associated with the device. These values represent commands or notifications that are supported under the KNX architecture for the device. It is not recommended to proceed with the implementation unless these values are obtained.
