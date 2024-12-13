# On test drive vehicle spawn

This event is triggered after a vehicle of test drive is spawned on the client doing the test drive

## Event

```lua
AddEventHandler("dealerships_creator:testDrive:vehicleSpawned", function(vehicle, vehicleNetId, plate)

end)
```

### Parameters

| Name           | Data Type | Description            |
| -------------- | --------- | ---------------------- |
| `vehicle`      | integer   | The vehicle handle     |
| `vehicleNetId` | integer   | The vehicle network ID |
| `plate` | string   | The vehicle's plate |

## Example

```lua
EventHandler("dealerships_creator:testDrive:vehicleSpawned", function(vehicle, vehicleNetId, plate)
    SetVehicleFuelLevel(vehicle, 100.0)

    -- You may want to give vehicle keys somehow
end)
```
