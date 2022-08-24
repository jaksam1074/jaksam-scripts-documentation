# Refresh player owned vehicles

## Refresh player owned vehicles

Using this export (from server side) will refresh the list of the player's owned vehicles (from owned\_vehicles on ESX or player\_vehicles on QBCore)

### Event

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(playerId, instantly)
```

### Parameters

## Give keys to identifier

| Name        | Data Type | Description                                                                                                                                                                        |
| ----------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `playerId`  | integer   | The player server ID                                                                                                                                                               |
| `instantly` | boolean   | OPTIONAL - By default, it will wait 2 seconds before actually refreshing, if you know for sure that you need it instantly, pass `true` as second parameter, otherwise can be empty |

### Example

```lua
RegisterNetEvent("vehicle_shop:playerBoughtVehicle", function(playerId, plate)
    -- This will refresh the player's owned vehicles after he buys a vehicle (just an example)

    exports["vehicles_keys"]:refreshPlayerOwnedVehicles(playerId)
end)
```
