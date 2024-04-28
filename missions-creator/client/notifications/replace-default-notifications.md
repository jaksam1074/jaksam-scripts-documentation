# Replace default notifications

Triggered after notifying player client side

## Event

```lua
AddEventHandler("missions_creator:notify", function(message, coloredMessage)

end)
```

### Parameters

| Name             | Data Type | Description                                                    |
| ---------------- | --------- | -------------------------------------------------------------- |
| `message`        | string    | Message of the notification but without \~r\~, \~g~~\~~~, etc. |
| `coloredMessage` | string    | Message of the notification                                    |

## Example

```lua
RegisterNetEvent("missions_creator:framework:ready", function() 
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["missions_creator"]:disableScriptEvent("missions_creator:notify")
end)

RegisterNetEvent("missions_creator:notify", function(message, coloredMessage)
    TriggerEvent("external_script:notify", message)
end)
```

## Where to insert the code?

You can place it in the file `jaksam_core/config/cl_config.lua`, **at the bottom of the file on new lines**
