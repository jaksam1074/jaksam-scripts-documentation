# Replace default notifications

Triggered after notifying player client side

## Event

```lua
AddEventHandler("farming_creator:notify", function(message, uncoloredMessage)

end)
```

### Parameters

| Name               | Data Type | Description                                                    |
| ------------------ | --------- | -------------------------------------------------------------- |
| `message`          | string    | Message of the notification                                    |
| `uncoloredMessage` | string    | Message of the notification but without \~r\~, \~g~~\~~~, etc. |

## Example

```lua
RegisterNetEvent("farming_creator:framework:ready", function() 
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["farming_creator"]:disableScriptEvent("farming_creator:notify")
end)

RegisterNetEvent("farming_creator:notify", function(message, uncoloredMessage)
    TriggerEvent("external_script:notify", message)
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
