# Replace default armory

Triggered when opening an armory

## Event

```lua
AddEventHandler("jobs_creator:armory:openArmory", function(markerId, armoryData)

end)
```

### Parameters

| Name         | Data Type | Description                                           |
| ------------ | --------- | ----------------------------------------------------- |
| `markerId`   | int       | Marker ID                                             |
| `armoryData` | table     | Contains some options you may use in external scripts |

## Example

```lua
RegisterNetEvent("jobs_creator:framework:ready", function() 
    -- Disables the default script armory
    exports["jobs_creator"]:disableScriptEvent("jobs_creator:armory:openArmory")
end)

-- Example to replace the script armory with an external one
RegisterNetEvent("jobs_creator:armory:openArmory", function(markerId, armoryData)
    --[[
        This is just an example, it will NOT work, you have to use the event from your inventory
    ]]
    TriggerEvent("inventory:openArmory", markerId)
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**

## OX Inventory

OX inventory has an easy integration in the file `jobs_creator/integrations/sh_integrations.lua`

## Quasar Inventory

Quasar Inventory has an easy integration in the file `jobs_creator/integrations/sh_integrations.lua`
