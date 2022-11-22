# Replace default police alert

Triggered when police is alerted

## Event

```lua
RegisterNetEvent("farming_creator:alertedPolice", function(coords, message)

end)
```

### Parameters

| Name      | Data Type | Description                                    |
| --------- | --------- | ---------------------------------------------- |
| `coords`  | vector3   | Coordinates where a player tried to sell drugs |
| `message` | string    | The message the cop would see                  |

## Example

```lua
-- Disables the default police alert
RegisterNetEvent("farming_creator:framework:ready", function() 
    exports["farming_creator"]:disableScriptEvent("farming_creator:alertedPolice")
end)

RegisterNetEvent("farming_creator:alertedPolice", function(coords, message)
    -- Do something
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
