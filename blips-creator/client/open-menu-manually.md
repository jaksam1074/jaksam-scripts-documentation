# Open menu manually

## Event

```lua
TriggerEvent("blips_creator:openBlipsMenu")
```

## Description

You can use this event from anywhere **client side** to open the menu

## Example

You can open the menu with a command with the following example

```lua
RegisterCommand("blipscreator", function() 
    TriggerEvent("blips_creator:openBlipsMenu")
end)
```
