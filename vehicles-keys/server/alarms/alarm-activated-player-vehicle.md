# Alarm activated (player vehicle)

Triggered when an alarm on a player vehicle is activated

## Event

```lua
RegisterNetEvent("vehicles_keys:alarmOnPlayerVehicle", function(vehicle, vehicleCoords, alarmLevel)

end)
```

### Parameters

| Name            | Data Type | Description                      |
| --------------- | --------- | -------------------------------- |
| `vehicle`       | int       | Vehicle handle                   |
| `vehicleCoords` | vector3   | The coordinates of the vehicle   |
| `alarmLevel`    | int       | The level of the installed alarm |

## Example

```lua
RegisterNetEvent("vehicles_keys:alarmOnPlayerVehicle", function(vehicle, vehicleCoords, alarmLevel)
    -- You can add an external notification if you want
end)
```

## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
