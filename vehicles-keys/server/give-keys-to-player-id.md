# Give keys to player ID

## Export

```lua
exports["vehicles_keys"]:giveVehicleKeysToPlayerId(playerId, plate, type)
```

### Parameters

| Name       | Data Type         | Description                                                                                               |
| ---------- | ----------------- | --------------------------------------------------------------------------------------------------------- |
| `playerId` | integer           | The target player server ID                                                                               |
| `plate`    | string            | The vehicle plate                                                                                         |
| `type`     | string (optional) | The vehicle type. The default will be "temporary". Available types: "temporary", "owned", "other\_player" |

## Example

```lua
RegisterNetEvent("vehicle_shop:playerBoughtVehicle", function(playerId, plate)
    exports["vehicles_keys"]:giveVehicleKeysToPlayerId(playerId, plate, "owned")
end)
```
