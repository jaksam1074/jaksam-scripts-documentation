# Replace default police alert

Triggered when police is alerted, this is triggered on each police player client, if you are looking for a single event, check the server side category

## Event

```lua
RegisterNetEvent("doors_creator:alertedPolice", function(coords, message)

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
RegisterNetEvent("doors_creator:framework:ready", function() 
    exports["doors_creator"]:disableScriptEvent("doors_creator:alertedPolice")
end)

RegisterNetEvent("doors_creator:alertedPolice", function(coords, message)
    -- Do something
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
