# Progress bar

## How to replace it?

You can use Jobs Creator [modules.md](modules.md "mention") if you want to use your own progress bar

## Use in external scripts

If you like the default progress bar of the script, and you want to use it in external scripts, this is the event

```lua
TriggerEvent("jobs_creator:startProgressBar", timeInMS, text, hexColor)
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
    TriggerEvent("jobs_creator:startProgressBar", tonumber(args[1]), args[2], "#ff0000")
end)
```
