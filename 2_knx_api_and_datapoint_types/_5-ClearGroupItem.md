## CLEAR\_GROUP\_ITEM

This function is used to remove **all** of the group items (tParams) that have been previously registered with the KNX Network driver.


###### Available from 8.0


### Signature

`C4:SendToProxy(num,”CLEAR_GROUP_ITEM”,tParams) `


| Parameters  | Description |
| --- | --- |
| `DEVICE_ID` | This is the Device ID of your driver. |


### Example

This example was taken from the KNX Generic driver: 

```lua
local tParams = {}
tParams["DEVICE_ID"] = C4:GetDeviceID()
C4:SendToProxy(1, ”CLEAR_GROUP_ITEM”, tParams)
```
