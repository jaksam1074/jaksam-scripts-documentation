# On vehicle bought

Triggered when a player buys a vehicle from buyable garage marker

## Event

```lua
RegisterNetEvent("jobs_creator:permanent_garage:vehicleBought", function(playerId, markerId, vehicleName, vehicleId)

end)
```

### Parameters

| Name          | Data Type | Description                |
| ------------- | --------- | -------------------------- |
| `playerId`    | integer   | Player's server ID         |
| `markerId`    | integer   | Marker ID                  |
| `vehicleName` | string    | Vehicle model name         |
| `vehicleId`   | integer   | Vehicle id in the database |

## Example

```lua
RegisterNetEvent("jobs_creator:permanent_garage:vehicleBought", function(playerId, markerId, vehicleName, vehicleId)
    print("Player ID :" .. playerId .. " bought a " .. vehicleName .. " with ID " .. vehicleId .. " from marker " .. markerId)
end)
```
