# Player lockpicked a vehicle

Triggered when a vehicle has been hotwired

## Event

```lua
RegisterNetEvent("vehicles_keys:playerLockpickedVehicle", function(playerId, vehicleNetId)

end)
```

### Parameters

| Name           | Data Type | Description        |
| -------------- | --------- | ------------------ |
| `playerId`     | int       | Player server ID   |
| `vehicleNetId` | int       | Vehicle network ID |

## Example

```lua
RegisterNetEvent("vehicles_keys:playerLockpickedVehicle", function(playerId, vehicleNetId)
    local vehicle = NetworkGetEntityFromNetworkId(vehicleNetId)
    
    print("The player " .. GetPlayerName(playerId) .. " has just lockpicked a vehicle with model " .. GetEntityModel(vehicle))
end)
```

## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
