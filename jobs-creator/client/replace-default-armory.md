# Replace default armory

Triggered when opening an armory

## Event

```lua
AddEventHandler("jobs_creator:armory:openArmory", function(markerId)

end)
```

### Parameters

| Name       | Data Type | Description |
| ---------- | --------- | ----------- |
| `markerId` | int       | Marker ID   |

## Example

```lua
RegisterNetEvent("jobs_creator:framework:ready", function() 
    -- Disables the default script armory
    exports["jobs_creator"]:disableScriptEvent("jobs_creator:armory:openArmory")
end)

-- Example to replace the script armory with an external one
RegisterNetEvent("jobs_creator:armory:openArmory", function(markerId)
    -- Example with Chezza's inventory
    TriggerEvent('inventory:open', {
        id = "marker_" .. markerId,
        type = "esx_job_creator_armory",
        title = 'Armory - ' .. markerId,
        weight = 1000,
        save = true,
        timeout = 1000
    })
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**

## OX Inventory

OX inventory has an easy integration in the file `jobs_creator/integrations/sh_integrations.lua`

## Quasar Inventory

Quasar Inventory has an easy integration in the file `jobs_creator/integrations/sh_integrations.lua`
