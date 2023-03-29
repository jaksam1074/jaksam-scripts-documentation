# Alarm activated (NPC vehicle)

Triggered when an alarm is triggered on a NPC vehicle

## Event

```lua
RegisterNetEvent("vehicles_keys:alarmOnNPCVehicle", function(vehicle, vehicleCoords)

end)
```

### Parameters

| Name            | Data Type | Description                    |
| --------------- | --------- | ------------------------------ |
| `vehicle`       | int       | Vehicle handle                 |
| `vehicleCoords` | vector3   | The coordinates of the vehicle |

## Example

```lua
RegisterNetEvent("vehicles_keys:alarmOnNPCVehicle", function(vehicle, vehicleCoords)
    -- You can add an external notification if you want
end)
```

## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
