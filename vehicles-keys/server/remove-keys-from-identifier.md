# Remove keys from identifier

## Export

```lua
exports["vehicles_keys"]:removeKeysFromIdentifier(identifier, plate)
```

### Parameters

| Name         | Data Type | Description                  |
| ------------ | --------- | ---------------------------- |
| `identifier` | string    | The target player identifier |
| `plate`      | string    | The vehicle plate            |

## Example

```lua
RegisterNetEvent("garage:vehicleDeleted", function(playerId, plate)
    local xPlayer = ESX.GetPlayerFromId(playerId)
    local identifier = xPlayer.identifier

    exports["vehicles_keys"]:removeKeysFromIdentifier(identifier, plate)
end)
```
