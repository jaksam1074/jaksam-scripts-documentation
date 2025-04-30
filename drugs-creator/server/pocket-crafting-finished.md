# Pocket Crafting Finished

This event is triggered when a player completes a pocket crafting process.

## Event Name
```lua
"drugs_creator:pocketCraftingFinished"
```

## Parameters
| Name | Type | Description |
|------|------|-------------|
| playerId | number | The server ID of the player who completed the crafting |
| itemName | string | The name of the pocket crafting item that was used |

## Description
This event is triggered after a player successfully completes a pocket crafting process. It is fired right after the player receives their crafted item.

## Example Usage
```lua
AddEventHandler("drugs_creator:pocketCraftingFinished", function(playerId, itemName)
    print("Player " .. playerId .. " finished crafting with " .. itemName)
end)
``` 