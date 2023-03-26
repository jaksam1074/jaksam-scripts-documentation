# Progress bar

## Replace/Disable

Triggered when using progress bar

### Event

```lua
RegisterNetEvent("robberies_creator:internalProgressBar", function(time, text)

end)
```

### Parameters

| Name   | Data Type | Description                      |
| ------ | --------- | -------------------------------- |
| `time` | int       | Progress bar duration in seconds |
| `text` | string    | Description text                 |

### Example

```lua
-- In robberies_creator/integrations/cl_integrations.lua
RegisterNetEvent("robberies_creator:framework:ready", function() 
    -- Disables the default script progress bar (otherwise there would be 2 progress bars)
    exports["robberies_creator"]:disableScriptEvent("robberies_creator:internalProgressBar")
end)

-- Example to replace the script progress bar with an external one
RegisterNetEvent("robberies_creator:internalProgressBar", function(time, text)
    -- The event to activate your external progress bar
    TriggerEvent("external_progressbar:start", time, text)
end)
```

### Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**

## Use in external scripts

If you like the default progress bar of the script, and you want to use it in external scripts, this is the event

```lua
TriggerEvent("robberies_creator:startProgressBar", timeInMS, text, hexColor)
```

### Parameters

| Name       | Data type | Description                                                                                                     |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------------- |
| `timeInMS` | integer   | Duration of the progress bar in milliseconds                                                                    |
| `text`     | string    | The text that will be shown with the progressbar                                                                |
| `hexColor` | string    | The color of the progressbar in hex code (example `#70f2b4`). Can be `nil` to use the default one of the script |

### Example

```lua
-- This will create a command to show a red progressbar
-- /progressbar 5000 Hello
RegisterCommand("progressbar", function(playerId, args) 
    TriggerEvent("robberies_creator:startProgressBar", tonumber(args[1]), args[2], "#ff0000")
end)
```
