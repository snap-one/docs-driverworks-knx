## GET\_NETWORK\_VERSION

This function allows you to associate your driver to a specific version of the KNX Network driver. It will provide your driver with the network version of the KNX Network Driver. Use this API only if your driver requires a specific version of the KNX Network driver.

Upon receiving the `GET_NETWORK_VERSION` request from your driver, The Network Driver will send a `NETWORK_VERSION `command back to your driver. Your driver will need to handle the `NETWORK_VERSION` command within the ExecuteCommand function.



###### Available from 8.0


### Signature

`C4:SendToProxy(num, ”GET_NETWORK_VERSION”, tParams) `


| Parameters  | Description |
| --- | --- |
| `DEVICE_ID` | This is the Device ID of your driver. |


### Example

Example 1 details sending the `GET_NETWORK_VERSION` function to the network Driver:

```lua
--Example 1

local tParams = {}
tParams["DEVICE_ID"] = C4:GetDeviceID()
C4:SendToProxy(1, "GET_NETWORK_VERSION", tParams)
```


Example 2 details how your driver should receive the response from the Network Driver:

```lua
-- Example 2

function EX_CMD.NETWORK_VERSION(tParams)
	dbgFunction("EX_CMD.NETWORK_VERSION()")
	dbgParams(tParams)

	gNetworkVersion = tonumber(tParams["VERSION"])
	
	if (gNetworkVersion < SUPPORTED_NETWORK_VERSION) then
		local errorMessage = "WARNING: KNX Network Driver version = " .. gNetworkVersion .. ". KNX Network Driver version should be " .. SUPPORTED_NETWORK_VERSION .. " or greater."
		C4:UpdateProperty("Driver Status", errorMessage)
		dbg(errorMessage)
	end
end
```
