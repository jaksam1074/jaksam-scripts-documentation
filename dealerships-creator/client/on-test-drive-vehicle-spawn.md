# On test drive vehicle spawn

This event is triggered after a vehicle of test drive is spawned on the client doing the test drive

## Event

```lua
AddEventHandler("dealerships_creator:testDrive:vehicleSpawned", function(vehicle, vehicleNetId)

end)
```

### Parameters

| Name           | Data Type | Description            |
| -------------- | --------- | ---------------------- |
| `vehicle`      | integer   | The vehicle handle     |
| `vehicleNetId` | integer   | The vehicle network ID |

## Example

```lua
EventHandler("dealerships_creator:testDrive:vehicleSpawned", function(vehicle, vehicleNetId)
    SetVehicleFuelLevel(vehicle, 100.0)
end)
```
