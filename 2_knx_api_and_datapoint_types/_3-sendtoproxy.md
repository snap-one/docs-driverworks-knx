## The Role of SendToProxy

Before discussing the use of the APIs, it is important to understand several concepts that they all share. As you review the API content you will notice that API’s are sent from your driver using the standard Control4 function: SendToProxy. SendToProxy requires two additional parameters in addition to the API. These include the KNX connection value and a table of parameters. For example:

`C4:SendToProxy(<connection value>,”<command>”,<table of parameters>)`

or

`C4:SendToProxy(1,”ADD-GROUP_ITEM”,tParams)`

The connection value in the examples above is the value assigned to the KNX ID value in the connections section of your driver. The \<id\>1\</id\> line in the sample below contains the connection value required by SendToProxy. The code example to the right comes from the KNX Network driver:


```xml
<connection>
      <id>1</id>
      <facing>6</facing>
      <connectionname>KNX Control</connectionname>
      <type>1</type>
      <consumer>True</consumer>
      <audiosource>False</audiosource>
      <videosource>False</videosource>
      <linelevel>True</linelevel>
      <classes>
        <class>
          <classname>KNX_DEVICE</classname>
          <autobind>True</autobind>
        </class>
      </classes>
</connection>
```


The table of parameters required by SendToProxy consists of a set (or at times a subset) of KNX Object Functions that are unique to your driver, the device it supports and the Datapoint Types you are using. The table elements are:

| Element  | Description |
| --- | --- |
| `GROUP_ADDRESS` | This is the KNX Group Address for the Object Function. |
| `DEVICE_ID` | This is the Device ID of your driver. |
| `PROPERTY` | This is the Property Name in Composer where the Group Address is stored. |
| `DATA_POINT_TYPE`  | The Data Point Type (DPT) required by the Object Function. |

The example to the right shows how the table elements are assembled in conjunction with a connection Id value of 1 and the `ADD_GROUP_ITEM` API:

```lua
local tParams = {}
tParams["GROUP_ADDRESS"] = Properties[“Channel 1 Address”]
tParams["DEVICE_ID"] = C4:GetDeviceID()
tParams["PROPERTY"] = “Channel 1 Address”
tParams["DATA_POINT_TYPE"] = “DPT_1”
C4:SendToProxy(1, ”ADD_GROUP_ITEM”, tParams)
```

