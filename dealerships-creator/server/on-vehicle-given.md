# On vehicle given

This event is triggered after a player receives a vehicle in any way

## Event

```lua
AddEventHandler("dealerships_creator:giveVehicleToPlayerId", function(playerId, vehicleName, plate)

end)
```

### Parameters

| Name          | Data Type | Description                                   |
| ------------- | --------- | --------------------------------------------- |
| `playerId`    | integer   | The player server ID who received the vehicle |
| `vehicleName` | string    | The vehicle spawn name                        |
| `plate`       | string    | The vehicle's plate                           |

## Example

```lua
AddEventHandler("dealerships_creator:giveVehicleToPlayerId", function(playerId, vehicleName, plate)
    -- Do anything you want
end)
```
