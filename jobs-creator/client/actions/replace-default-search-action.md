# Replace default search action

Triggered when searching in a player inventory

## Event

```lua
RegisterNetEvent("jobs_creator:actions:search:searchPlayer", function(targetServerId)

end)
```

### Parameters

| Name             | Data Type | Description                 |
| ---------------- | --------- | --------------------------- |
| `targetServerId` | integer   | The target player server ID |

## Example

```lua
RegisterNetEvent("jobs_creator:framework:ready", function() 
    -- Disables the default script search (otherwise there would be 2 searches)
    exports["jobs_creator"]:disableScriptEvent("jobs_creator:actions:search:searchPlayer")
end)

RegisterNetEvent("jobs_creator:actions:search:searchPlayer", function(targetServerId)
    TriggerEvent("external_script:searchInPlayerInventory", targetServerId)
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
