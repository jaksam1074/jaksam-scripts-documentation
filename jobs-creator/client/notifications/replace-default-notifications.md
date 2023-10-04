# Replace default notifications

Triggered after notifying player client side

## Event

```lua
RegisterNetEvent("jobs_creator:notify", function(message, coloredMessage)

end)
```

### Parameters

| Name             | Data Type | Description                                                          |
| ---------------- | --------- | -------------------------------------------------------------------- |
| `message`        | string    | Message of the notification                                          |
| `coloredMessage` | string    | Message of the notification but with \~r\~, \~g~~\~~~, etc. included |

## Example

```lua
RegisterNetEvent("jobs_creator:framework:ready", function() 
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["jobs_creator"]:disableScriptEvent("jobs_creator:notify")
end)

RegisterNetEvent("jobs_creator:notify", function(message, coloredMessage)
    TriggerEvent("external_script:notify", message)
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
