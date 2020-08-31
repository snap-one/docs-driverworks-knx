## ADD\_GROUP\_ITEM

This function is used to register each of KNX Object Functions required for your driver, with the KNX Network driver. 


###### Available from 8.0


### Signature

`C4:SendToProxy(num, "ADD_GROUP_ITEM", tParams)`


| Parameters  | Description |
| --- | --- |
| `GROUP_ADDRESS` | This is the KNX Group Address for the Object Function. |
| `DEVICE_ID` | This is the Device ID of your driver. |
| `PROPERTY` | This is the Property Name in Composer where the Group Address is stored. |
| `DATA_POINT_TYPE`  | The Data Point Type (DPT) required by the Object Function. |
| `STARTUP_READ`  | Optional. If false, Group Address will not be read on startup. If omitted or set to true, Group Address will be read on startup. |


### Example

The example to the right shows how the table elements are assembled in conjunction with a connection Id value of 1 and the `ADD_GROUP_ITEM` API:

```lua
local tParams = {}
tParams["GROUP_ADDRESS"] = Properties[“Channel 1 Address”]
tParams["DEVICE_ID"] = C4:GetDeviceID()
tParams["PROPERTY"] = “Channel 1 Address”
tParams["DATA_POINT_TYPE"] = “DPT_1”
C4:SendToProxy(1, ”ADD_GROUP_ITEM”, tParams)
```
