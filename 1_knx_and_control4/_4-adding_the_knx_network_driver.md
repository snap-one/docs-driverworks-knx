## Adding the KNX Network Driver

The first step in including KNX certified devices into your Control4 project is the inclusion of the KNX Network driver. The Network driver serves as a layer between the KNX modules and the control devices (dimmers, switch, keypad.) in your project. It handles the parsing of commands sent from the devices and passes them on via Ethernet connection to the KNX modules. Similarly, it handles communication from the modules to the control devices.


<img src="images/1_4-01.png"/>


The preferred path in implementing KNX within Composer Pro is to add the KNX Network driver to your project PRIOR to adding any KNX device drivers that you wish to control or monitor in your system. By adding the Network driver first, all of the KNX device drivers subsequently added will be automatically bound correctly to the network driver in the Connections area of Composer Pro.
Any KNX device drivers added to the project prior to the KNX Network driver will need to be manually bound in the Connections area of Composer Pro.


<img src="images/1_4-02.png"/>

The following screen shot is populated KNX Network Driver Properties page:

<img src="images/1_4-03.png"/>


In the above example, the KNX Network driver has been added to the project. Configuration points provided under Properties page include:

**KNX Gateway Address**: The address represents the physical IP address of the KNX Gateway device used in your project.

**KNX Delay:** This is an editable time value that ranges from 0 to 500 milliseconds. It defaults to 0, which is OFF. This setting represents the time allotted for a KNX command to be sent. For example, consider a Control4 project that has 10 KNX light switches. A lighting scene is configured to turn off all of the lights with the push of a keypad button. If the KNX delay value is set to 100 milliseconds at most each off command will be sent at 100 millisecond intervals. The first command will be sent immediately upon the button push, followed by the second OFF command 100 milliseconds later and so on until all 10 OFF commands are sent. Manipulation of this value is particularly useful when large amounts of devices are in a system. In our example, while the OFF commands are being sent, OFF notifications are being received. If the commands are sent too quickly, a situation could arise where commands get dropped due to the influx of inbound notifications. Manipulation of this value is recommended when a performance lag occurs or commands are dropped.

**Connection Status:** This field is read only. It provides the current connection status with the KNX Server. It also provides error messages in the event that a connection issue arises. Supported errors include:

- Connection with KNXnet/IP Server successful.
- The KNXnet/IP Server device cannot find an active data connection with the specified ID."
- The requested connection type is not supported by the KNXnet/IP Server device
- One or more requested connection options are not supported by the KNXnet/IP Server device." The KNXnet/IP Server device cannot accept the new data connection because its maximum amount of concurrent connections is already occupied."
- The KNXnet/IP Server device detects an error concerning the data connection with the specified ID.
- The KNXnet/IP Server device detects an error concerning the KNX subnetwork connection with the specified ID."
- Unknown status from KNXnet/IP Server device (0x" .. string.format("%02x", status) 

**Port:** Default is 3671 – This value represents the port used by the KNX network driver for communication. Any networking changes that modify the default port value must be reflected here.

**Controller Address:** This a read only field that provides the address of the KNX Controller 


The Actions tab provides the ability to quickly connect to and disconnect from the KNX network driver. This can be useful when trouble shooting or testing the KNX devices in your project, especially if timers are used. Note that disconnecting through the button on the Actions tab requires you to re-connect through this screen. 

<img src="images/1_4-04.png"/>

**Display Globals:** This button will display a list of all global values associated with the driver. This is particularly useful when debugging drivers.

**Display Group Addresses:** This button will display a list of all of the Group Address that the network driver is aware of. The addresses are displayed with their associated Datapoint and Group ID values.
