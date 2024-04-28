# Replace default police alert

{% hint style="warning" %}
Triggered when police is alerted, this is triggered on each police player client, if you are looking for a single event, check the server side category
{% endhint %}

## Event

```lua
RegisterNetEvent("shops_creator:alertedPolice", function(coords, message)

end)
```

### Parameters

| Name      | Data Type | Description                                    |
| --------- | --------- | ---------------------------------------------- |
| `coords`  | vector3   | Coordinates where a player tried to sell drugs |
| `message` | string    | The message the cop will see                   |

## Example

```lua
-- Disables the default police alert
RegisterNetEvent("shops_creator:framework:ready", function() 
    exports["shops_creator"]:disableScriptEvent("shops_creator:alertedPolice")
end)

RegisterNetEvent("shops_creator:alertedPolice", function(coords, message)
    -- Do something
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
