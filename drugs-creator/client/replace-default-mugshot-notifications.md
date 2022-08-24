# Replace default mugshot notifications

Notification shown when a ped refuses the drug in NPC selling (notification with ped face)

## Event

```lua
AddEventHandler("advanced_drugs_creator:internalMugshotNotify", function(ped, title, message)

end)
```

### Parameters

| Name      | Data Type | Description                 |
| --------- | --------- | --------------------------- |
| `ped`     | int       | Ped entity handle           |
| `title`   | string    | Title of the notification   |
| `message` | string    | Message of the notification |

## Example

```lua
RegisterNetEvent("advanced_drugs_creator:framework:ready", function() 
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["advanced_drugs_creator"]:disableScriptEvent("advanced_drugs_creator:internalMugshotNotify")
end)

RegisterNetEvent("advanced_drugs_creator:internalMugshotNotify", function(ped, title, message)
    TriggerEvent("external_script:notify", message)
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
