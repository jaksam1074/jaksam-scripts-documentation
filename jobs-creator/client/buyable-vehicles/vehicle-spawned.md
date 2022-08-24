# Vehicle spawned

Triggered after the spawn of a bought vehicle from buyable vehicles garage

## Event

```lua
AddEventHandler("jobs_creator:permanent_garage:vehicleSpawned", function(vehicle, vehicleName, vehiclePlate)

end)
```

### Parameters

| Name           | Data Type      | Description          |
| -------------- | -------------- | -------------------- |
| `vehicle`      | vehicle handle | The vehicle's handle |
| `vehicleName`  | string         | The vehicle's name   |
| `vehiclePlate` | string         | Vehicle's plate      |

## Example

```lua
AddEventHandler("jobs_creator:permanent_garage:vehicleSpawned", function(vehicle, vehicleName, vehiclePlate)

    -- Example to give keys to the vehicle (you may have a TriggerEvent to use, that's up to you)
    giveKeysToVehicle(vehicle)

    print(vehicleName) -- Example output 'adder'
end)
```
