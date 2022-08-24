# Replace default notifications

Triggered after notifying player client side

## Event

```lua
AddEventHandler("billing_ui:notify", function(message)

end)
```

### Parameters

| Name      | Data Type | Description                 |
| --------- | --------- | --------------------------- |
| `message` | string    | Message of the notification |

## Example

```lua
RegisterNetEvent("billing_ui:framework:ready", function() 
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["billing_ui"]:disableScriptEvent("billing_ui:notify")
end)

RegisterNetEvent("billing_ui:notify", function(message)
    TriggerEvent("external_script:notify", message)
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
