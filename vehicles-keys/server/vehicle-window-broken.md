# Vehicle window broken

## Event

```lua
RegisterNetEvent("vehicles_keys:vehicleWindowBroken", function(playerId, vehicleNetId)

end)
```

### Parameters

| Name           | Data Type        | Description                               |
| -------------- | ---------------- | ----------------------------------------- |
| `playerId`     | integer          | The player server ID who broke the window |
| `vehicleNetId` | integer (net ID) | The vehicle network ID                    |

## Example

```lua
RegisterNetEvent("vehicles_keys:vehicleWindowBroken", function(playerId, vehicleNetId)
    local vehicle = NetworkGetEntityFromNetworkId(vehicleNetId)

    print(GetPlayerName(playerId) .. " broke the window of plate " .. GetVehicleNumberPlateText(vehicle))
end)
```
