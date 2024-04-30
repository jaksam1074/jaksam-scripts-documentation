# On entity spawn

## Event

```lua
RegisterNetEvent("missions_creator:entitySpawned", function(entityType, entity)
    
end)
```

### Parameters

| Name         | Data Type | Description                  |
| ------------ | --------- | ---------------------------- |
| `entityType` | string    | `ped` / `vehicle` / `object` |
| `entity`     | integer   | The entity's handle          |

## Example

```lua
-- Just an example you can edit to give keys to spawned vehicles
RegisterNetEvent("missions_creator:entitySpawned", function(entityType, entity) 
    if(entityType == "vehicle") then
        local plate = GetVehicleNumberPlateText(entity)
        TriggerEvent("GIVEKEYS", plate)
    end
end)
```

## Where to insert the code?

You can place it in the file `jaksam_core/config/cl_config.lua`, **at the bottom of the file on new lines**
