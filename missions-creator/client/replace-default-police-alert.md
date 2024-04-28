# Replace default police alert

{% hint style="warning" %}
Triggered when police is alerted, this is triggered on each police player client, if you are looking for a single event, check the server side category
{% endhint %}

## Event

```lua
RegisterNetEvent("missions_creator:alertedPolice", function(coords, message)

end)
```

### Parameters

| Name      | Data Type | Description                   |
| --------- | --------- | ----------------------------- |
| `coords`  | vector3   | Coordinates to send to police |
| `message` | string    | The message the cop will see  |

## Example

```lua
-- Disables the default police alert
RegisterNetEvent("missions_creator:framework:ready", function() 
    exports["missions_creator"]:disableScriptEvent("missions_creator:alertedPolice")
end)

RegisterNetEvent("missions_creator:alertedPolice", function(coords, message)
    -- Do something
end)
```

## Where to insert the code?

You can place it in the file `jaksam_core/config/cl_config.lua`, **at the bottom of the file on new lines**
