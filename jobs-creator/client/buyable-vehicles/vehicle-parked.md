# Vehicle parked

Triggered after the vehicle from buyable vehicles garage has been parked

## Event

```lua
AddEventHandler("jobs_creator:permanent_garage:vehicleParked", function(vehicleModel, vehiclePlate)

end)
```

### Parameters

| Name           | Data Type | Description                |
| -------------- | --------- | -------------------------- |
| `vehicleModel` | integer   | The vehicle's entity model |
| `vehiclePlate` | string    | Vehicle's plate            |
