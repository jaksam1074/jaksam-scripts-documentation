# Replace default police alert

{% hint style="warning" %}
Triggered when police is alerted, this is triggered on each police player client, if you are looking for a single event, check the server side category
{% endhint %}

## Event

```lua
RegisterNetEvent("robberies_creator:alertedPolice", function(coords, message)

end)
```

### Parameters

| Name      | Data Type | Description                      |
| --------- | --------- | -------------------------------- |
| `coords`  | vector3   | Coordinates where crime happened |
| `message` | string    | The message the cop will see     |

## Example

```lua
-- Disables the default police alert
RegisterNetEvent("robberies_creator:framework:ready", function() 
    exports["robberies_creator"]:disableScriptEvent("robberies_creator:alertedPolice")
end)

RegisterNetEvent("robberies_creator:alertedPolice", function(coords, message)
    -- Do something
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
