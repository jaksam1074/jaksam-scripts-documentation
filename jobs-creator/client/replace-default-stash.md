# Replace default stash

Triggered when opening a stash

## Event

```lua
RegisterNetEvent("jobs_creator:stash:openStash", function(markerId)

end)
```

### Parameters

| Name       | Data Type | Description |
| ---------- | --------- | ----------- |
| `markerId` | int       | Marker ID   |

## Example

```lua
RegisterNetEvent("jobs_creator:framework:ready", function() 
    -- Disables the default script stash
    exports["jobs_creator"]:disableScriptEvent("jobs_creator:stash:openStash")
end)

-- Example to replace the script stash with an external one
RegisterNetEvent("jobs_creator:stash:openStash", function(markerId)
    --[[
        This is just an example, it will NOT work, you have to use the event from your inventory
    ]]
    TriggerEvent("inventory:openStash", markerId)
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**

## OX Inventory

OX inventory has an easy integration in the file `jobs_creator/integrations/sh_integrations.lua`

## Quasar Inventory

Quasar Inventory has an easy integration in the file `jobs_creator/integrations/sh_integrations.lua`
