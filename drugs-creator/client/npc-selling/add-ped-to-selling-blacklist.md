# Add ped to selling blacklist

To add a ped to NPC selling blacklist, so players won't be able to sell to the ped (example: blackjack dealers, shop keepers, etc.)

If you prefer an easier way, you can blacklist entire ped models in `drugs_creator/integrations/cl_integrations.lua`

## Event

```lua
exports["drugs_creator"]:addPedToNPCSellingBlacklist(ped)
```

### Parameters

| Name  | Data Type     | Description             |
| ----- | ------------- | ----------------------- |
| `ped` | ped (integer) | The target ped's handle |

## Example

```lua
RegisterNetEvent('drugs_creator:framework:ready', function()
    local closestPed = ESX.Game.GetClosestPed()

    exports["drugs_creator"]:addPedToNPCSellingBlacklist(closestPed)
end)
```
