# Self give current vehicle plate

This event does the same thing as "[Self give vehicle plate](self-give-vehicle-plate.md)", but this is even easier since it doesn't require any parameter, it's just a copy paste line

Triggering this event will automatically find the vehicle the local player is driving, and it will give its keys to him

## Event

```lua
TriggerServerEvent("vehicles_keys:selfGiveCurrentVehicleKeys")
```

## Example

```lua
-- Just an event of a imaginary driving school script
RegisterNetEvent("driving_school:test_started", function() 
    local vehicle = CreateVehicle("blista", 249.40, -1407.23, 30.40, true, false)
    SetVehicleColours(vehicle, 4, 5)
    SetVehicleExtraColours(vehicle, 1, 2)
    SetEntityHeading(vehicle, 317.64)
    SetVehicleOnGroundProperly(vehicle)
    SetPedIntoVehicle(PlayerPedId(), vehicle, -1)

    -- VEHICLES KEYS INTEGRATION TO GIVE THE KEYS EASILY
    TriggerServerEvent("vehicles_keys:selfGiveCurrentVehicleKeys")
end)
```
