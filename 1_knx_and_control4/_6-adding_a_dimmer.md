## Adding a Dimmer

To add a KNX enabled Dimmer to your project, you will need to add the knx\_dimmer.c4i driver. You will need to add the knx\_dimmer.c4i file to directory path for your other Lua based drivers.

This is typically: C:\Users\user\Documents\Control4\Drivers

Once added, you can open Composer Pro and find the driver under the Items area. Click on the Search tab and select Local Database. Using Device Type of “Light” and the Manufacturer of “KNX” you will see the switch and dimmer drivers.

<img src="images/1_6-01.png"/>

Double click on the Dimmer driver to add it to your project. Clicking on the properties for the switch device will display the following screen:

<img src="images/1_6-02.png"/>

**Driver Status** – This field displays an error when an invalid group address is entered. Future implementation will include handling of more error messages provided by the network driver.

**Dimming Mode:** The Dimming Mode button supports two types of dimmer functionality: 
On/Off or Set Level.

On/Off is useful for dimmers that only have the ability to ramp up to 100% and then back down to 0% If your dimmer cannot ramp to a specified level, this value should be set to ON/Off. 

The Level value is the default value of the button. It should be set for dimmers that can ramp to a provided value. The Dimmer properties screen also allows you to enter the Set 
Address values for your Dimmer.

Feedback is accomplished with the Dimmer driver using the Status Address field. Adding the correct Group Address for this functionality will enable the Dimmer to provide Feedback on its current level of lighting.
Note: The version of this release currently does not support ramp-to-level functionality.
