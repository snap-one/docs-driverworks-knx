## REMOVE\_GROUP\_ITEM

This function is used to remove a pre-registered group item with the KNX network driver.


###### Available from 8.0


### Signature

`C4:SendToProxy(num, ”REMOVE_GROUP_ITEM”, tParams) `


| Parameters  | Description |
| --- | --- |
| `GROUP_ADDRESS` | This is the KNX Group Address for the Object Function. |
| `DEVICE_ID` | This is the Device ID of your driver. |
| `PROPERTY` | This is the Property Name in Composer where the Group Address is stored. |


### Example

```lua
local tParams = {}
tParams["GROUP_ADDRESS"] = Properties[“Channel 1 Address”]
tParams["DEVICE_ID"] = C4:GetDeviceID()
tParams["PROPERTY"] = “Channel 1 Address”
C4:SendToProxy(1, ”REMOVE_GROUP_ITEM”, tParams)
```
