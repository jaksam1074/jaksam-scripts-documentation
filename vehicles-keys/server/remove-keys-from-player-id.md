# Remove keys from player ID

## Export

```lua
exports["vehicles_keys"]:removeKeysFromPlayerId(playerId, plate)
```

### Parameters

| Name       | Data Type | Description                 |
| ---------- | --------- | --------------------------- |
| `playerId` | integer   | The target player server ID |
| `plate`    | string    | The vehicle plate           |

## Example

```lua
RegisterNetEvent("garage:vehicleDeleted", function(playerId, plate)
    exports["vehicles_keys"]:removeKeysFromPlayerId(playerId, plate)
end)
```
