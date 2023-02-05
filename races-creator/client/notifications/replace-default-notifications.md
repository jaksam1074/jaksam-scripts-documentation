# Replace default notifications

Triggered after notifying player client side

## Event

```lua
AddEventHandler("races_creator:notify", function(message, uncoloredMessage)

end)
```

### Parameters

| Name               | Data Type | Description                                                    |
| ------------------ | --------- | -------------------------------------------------------------- |
| `message`          | string    | Message of the notification                                    |
| `uncoloredMessage` | string    | Message of the notification but without \~r\~, \~g~~\~~~, etc. |

## Example

```lua
RegisterNetEvent("races_creator:framework:ready", function() 
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["races_creator"]:disableScriptEvent("races_creator:notify")
end)

RegisterNetEvent("races_creator:notify", function(message, uncoloredMessage)
    TriggerEvent("external_script:notify", message)

    -- OR if you DON'T want ~r~, ~g~ you can use 
    --TriggerEvent("external_script:notify", uncoloredMessage)
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
