# Replace default help notifications

Used to show the usual `Press E to ...` at the top left of the player's screen

## Export

```lua
exports["missions_creator"]:replaceShowHelpNotification(customFunction)
```

### Parameters

| Name             | Data Type | Description                                                                                                                                |
| ---------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `customFunction` | function  | A function that will replace the default ESX.ShowHelpNotification method. **Requires** the message parameter and will be called each frame |

## Example

```lua
local function myCustomHelpNotification(message)
    -- Customize your function to fit your needs
    print(message)

    ExternalScript.showHelpNotification(message)
end

RegisterNetEvent("missions_creator:framework:ready", function() 
    -- This will replace the base function with the one you want
    exports["missions_creator"]:replaceShowHelpNotification(myCustomHelpNotification)
end)
```

## Where to insert the code?

You can place it in the file `jaksam_core/config/cl_config.lua`, **at the bottom of the file on new lines**
