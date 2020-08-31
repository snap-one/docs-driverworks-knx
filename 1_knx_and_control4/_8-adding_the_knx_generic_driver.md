## Adding the KNX Generic Driver

To add the KNX Generic driver to your project, you will need to add the knx\_generic.c4i driver.  You will need to add the knx\_keypad.c4i file to directory path for your other Lua based drivers.

This is typically: C:\Users\user\Documents\Control4\Drivers

Once added, you can open Composer Pro and find the driver under the Items area. Click on the Search tab and select Local Database. Using Device Type of “other” and the Manufacturer of “KNX” you will see the Generic driver.

The generic driver is included as a means to control a device or get data from a device that currently has no driver. The driver provides a useful means to assign “Channels” of control which utilize KNX addresses and DataPoint Types to send KNX values to a device, receive KNX values or statuses from a device.

Once the driver is added, it is configured under the Lua Properties tab. When all of the desired control Channels have been configured, advanced programming (Actions, Events & Variables) can be created within ComposerPro to control a device as well as handle feedback from a devices.

**Configuring the KNX Generic Driver**
Once the Generic Driver has been added to your project you can open the driver’s properties page. This page is where all of the driver configuration will take place. The Properties page supports the creation of up to eight control “Channels”. Each channel has (at a minimum) the following fields:

**Channel # Data Point Type** – This field supports the assignment of the desired KNX Data Point Type (DPT) value.  DPTs currently supported include DPT\_1 through DPT\_14 and DPT\_16.

**Channel # Address** – This field contains the device’s KNX group address.

In the screen shot below, the Generic Driver’s property page is open. It defaults to having all eight available channels open. In our example, we will configure this instance of the Generic Driver to have four channels. To do this, we enter a 4 in the Number of Channels field and click on the Set button. 

<img src="images/1_8-01.png"/>

The Properties page now looks like this:

<img src="images/1_8-02.png"/>

Now that the desired amount of channels are defined, we can configure them to use various DPT values to handle various types of control scenarios. For purposes of example, we’ll use the Generic Driver to control a blind. To configure Channel 1 to use Data Point Type 1 for devices that have a Group Address of 1/0/10 our Properties page will look like this: 

<img src="images/1_8-03.png"/>

Note that in our example above we are assigning a Channel 1 Value of 1. Based on KNX documentation, we know that there are two possible values for Data Point Type 1: 0 or 1.

For Channel 2, we need to use Data Point Type value 3. DPT 3 supports directional control (down & up) as well as incremental changes in direction. Our Channel 2 configuration looks like this: 

<img src="images/1_8-04.png"/>

We are passing a direction value of 1(up) for this channel. We are also supplying a Step Code value. This value represents the percentage of change channel 2 will support. Our example shows 25%. This means that the control provided by Channel 2 will be an increase in our blind level by 25% from its present position.

For Channel 3, we’ll establish some scheduling control for our blind by adding Day, Hour, Minute and Second values by using Data Point Value 10. 

<img src="images/1_8-05.png"/>

Based on the values entered above, the current schedule value for Channel 3 is Monday (1), 3:30:07 PM (15) (30) (7).
Note that a day value of 0 results in no day being represented.

We can expand on our scheduling capabilities by using Data Point Value 11 which supports Day, Month and Year values. For example, a date value of July 6, 2013 would look like this:

<img src="images/1_8-06.png"/>

Now that we have configured all four Channels for this instance of the Generic driver the channels can be tested under the Actions tab:

<img src="images/1_8-07.png"/>

The Actions tab default to displaying all eight Channel configurations. By clicking on each of the four respective channels which we have configured we can test the configuration of the Channel itself.

**Composer Programming and the KNX Generic Driver**
One of the main purposes behind providing the KNX Generic driver is to support control of a device without having to write a dedicated driver for that device. Using the programming capabilities found in ComposerPro, we can trigger control scenarios based on three KNX based events. These events are:

**Matching Data Received** – This event occurs when the value that is assigned to a specific channel is received from the KNX Network. For example, we configured Channel 1 with a value of 1. When a 1 is received from the KNX network, this event can be used for programming purposes.

**Data Sent to KNX** – This event occurs when the data value for Channel 1 is sent to the KNX Network. For example, Channel 2 is configured with a Direction Value of 1 and a Step Code of 25. Programming can be based on the delivery of values 1 7 25 to the KNX Network.

**Data Received from KNX** – This event is similar to Matching Data Received in that it is based on receiving data from the KNX Network. This event is triggered whenever any data is received.from the KNX Network  All three of these programming events are available when you click on programming in ComposerPro for the KNX Generic Driver:

<img src="images/1_8-08.png"/>

Let’s consider some simple programming scenarios based of the three KNX based events available to use along with the way we have configured the KNX Generic Driver. In our first example, we have created programming to raise out blinds up when Channel 1 is activated. It will pass a value of 1 to the KNX Network and, through programming, cause our blinds to raise:

<img src="images/1_8-09.png"/>

We can also base programming off of receiving data from the KNX Network. Using Channel 1 as an example again, if we receive a value other than one we can trigger a programming event using the “Data Received from KNX” event definition. In the example below, if we receive any value other than a 1 from the network through Channel 1 we will lower the blinds: 

<img src="images/1_8-10.png"/>

Note that this example is similar to using the “Matching Data Received” event definition. If we were using “Matching Data Received” (a value of 1 in our example) we would program our blinds to rise.

Since we have configured our generic Driver with some scheduling related Data point Types we can program an event off of a time. For example, if we use “Matching Data Received” for Channel 3 we can raise or lower our blinds at a certain time. We configured Channel 3’s value for Monday 3:30:07 PM or (1) (15) (30) (7). The programming below will lower our blinds (if they are up) when the matching values are received from the KNX Network: 

<img src="images/1_8-11.png"/>


**Using Variables with the KNX Generic Driver**
If you open the KNX Generic Driver under Programming, you will see all of the variables that are currently available for KNX. By default, Programming populates all of the available variables for a channel. It also provides these variables for a complete set of eight channels. For example, the variables available for Channel\_1 include:\_

<img src="images/1_8-12.png"/>

Note that while all variables are displayed, only variables applicable to the Data Point Type configured for the channel under the Properties page will support programming. For example, the CHANNEL\_1\_STEP variable for Channel 1will not work if DPT\_1 is configured. 

Through the use of variable, it is possible to base programming off sending data to KNX, receiving data from KNX and receiving matching data from KNX. For example, the screen shot below shows variable-based programming when data is sent through Channel 1 of our KNX Generic Driver. Based on the information in the previous section, Channel 1 uses DPT\_1 which in turn, supports passing values 0 & 1 to KNX.\_

<img src="images/1_8-13.png"/>

In the example above, when data is sent to KNX through Channel 1we will toggle Light 3 in the Theater Room through the use of a Command. It is worth noting that when using variable based programming in conjunction with the “Data Received from KNX” generic event the value that will be used by the variable is that actual value received from KNX as opposed to the value configured for the channel in the Properties page. Conditionals and Loops are also available as programming options.
