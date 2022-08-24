# Vehicle parked

Triggered after the vehicle from temporary garage has been parked

## Event

```lua
AddEventHandler("jobs_creator:temporary_garage:vehicleParked", function(vehicleModel, vehiclePlate)

end)
```

### Parameters

| Name           | Data Type | Description                |
| -------------- | --------- | -------------------------- |
| `vehicleModel` | integer   | The vehicle's entity model |
| `vehiclePlate` | string    | Vehicle's plate            |
