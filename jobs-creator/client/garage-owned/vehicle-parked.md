# Vehicle parked

Triggered after the vehicle from owned vehicles garage has been parked

## Event

```lua
AddEventHandler("jobs_creator:garage_owned:vehicleParked", function(vehicleModel, vehiclePlate)

end)
```

### Parameters

| Name           | Data Type | Description                |
| -------------- | --------- | -------------------------- |
| `vehicleModel` | integer   | The vehicle's entity model |
| `vehiclePlate` | string    | Vehicle's plate            |
