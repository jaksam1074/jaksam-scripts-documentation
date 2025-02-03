# UI Toggled
Useful to hide/show your UI when the shop UI is toggled

## Shop UI actived

```lua
RegisterNetEvent("shops_creator:ui:show", function()
    -- Disable here your UI with your own code
end)

```
## Shop UI disabled

```lua
RegisterNetEvent("shops_creator:ui:hide", function()
    -- Enable here your UI with your own code
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
