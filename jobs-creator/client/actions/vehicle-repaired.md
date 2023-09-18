# Vehicle repaired

Triggered after a vehicle is repaired with job actions menu, useful if you want to add an extra repair function to the current ones

## Event

```lua
AddEventHandler("jobs_creator:vehicleRepaired", function(vehicle)
    -- You can add the extra repair functions here
end)
```

### Parameters

| Name      | Data Type      | Description          |
| --------- | -------------- | -------------------- |
| `vehicle` | vehicle handle | The vehicle's handle |
