## REQUEST\_STATUS

This function allows you to query the KNX system for the status of an Object Function. The KNX Dimmer and KNX Switch drivers provide examples of using this function.


###### Available from 8.0


### Signature

`C4:SendToProxy(num, ”REQUEST_STATUS”, tParams) `


| Parameters  | Description |
| --- | --- |
| `GROUP_ADDRESS` | This is the KNX Group Address for the Object Function. |


### Example

```lua
local tParams = {}
tParams["GROUP_ADDRESS"] = Properties[“Channel 1 Address”]
C4:SendToProxy(1, ”REQUEST_STATUS”, tParams)
```
