# Replace/Disable default progress bar

Triggered when using progress bar

## Event

```lua
RegisterNetEvent("robberies_creator:internalProgressBar", function(time, text)

end)
```

### Parameters

| Name   | Data Type | Description                      |
| ------ | --------- | -------------------------------- |
| `time` | int       | Progress bar duration in seconds |
| `text` | string    | Description text                 |

## Example

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

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
