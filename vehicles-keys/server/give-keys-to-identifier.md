# Give keys to identifier

## Export

```lua
exports["vehicles_keys"]:giveVehicleKeysToIdentifier(identifier, plate, type)
```

### Parameters

| Name         | Data Type         | Description                                                                                               |
| ------------ | ----------------- | --------------------------------------------------------------------------------------------------------- |
| `identifier` | string            | The target player identifier/license                                                                      |
| `plate`      | string            | The vehicle plate                                                                                         |
| `type`       | string (optional) | The vehicle type. The default will be "temporary". Available types: "temporary", "owned", "other\_player" |

## Example

```lua
RegisterNetEvent("vehicle_shop:playerBoughtVehicle", function(playerId, plate)
    local xPlayer = ESX.GetPlayerFromId(playerId)
    local identifier = xPlayer.identifier

    exports["vehicles_keys"]:giveVehicleKeysToIdentifier(identifier, plate, "owned")
end)
```
