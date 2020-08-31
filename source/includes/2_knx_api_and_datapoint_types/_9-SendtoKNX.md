## SEND\_TO\_KNX

This function is used to send commands to the KNX system based on Data Point Types (DPTs) and group address. 


###### Available from 8.0


### Signature

`C4:SendToProxy(1, ”SEND_TO_KNX”, tParams)`


| Parameters  | Description |
| --- | --- |
| `GROUP_ADDRESS` | This is the KNX Group Address for the Object Function. |
| `DATA_POINT_TYPE`  | The Data Point Type (DPT) required by the Object Function. |

Note that all other potential parameters are dependent on the DPT being used.


### Example

```lua
local tParams = {}
tParams["GROUP_ADDRESS"] = Properties[“Channel 1 Address”]
tParams["DATA_POINT_TYPE"] = “DPT_1”
tParams[“VALUE”] = 1
C4:SendToProxy(1, ”SEND_TO_KNX”, tParams)
```
