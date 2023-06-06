# Replace default notifications

Triggered after notifying player client side

## Event

```lua
AddEventHandler("drugs_creator:notify", function(message, uncoloredMessage)

end)
```

### Parameters

| Name               | Data Type | Description                                                    |
| ------------------ | --------- | -------------------------------------------------------------- |
| `message`          | string    | Message of the notification                                    |
| `uncoloredMessage` | string    | Message of the notification but without \~r\~, \~g~~\~~~, etc. |

## Example

```lua
RegisterNetEvent("drugs_creator:framework:ready", function() 
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["drugs_creator"]:disableScriptEvent("drugs_creator:notify")
end)

RegisterNetEvent("drugs_creator:notify", function(message, uncoloredMessage)
    TriggerEvent("external_script:notify", message)
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
