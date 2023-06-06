# Remove ped from selling blacklist

To remove a ped from NPC selling blacklist, the opposite of the export `addPedToNPCSellingBlacklist`

## Event

```lua
exports["drugs_creator"]:removePedFromNPCSellingBlacklist(ped)
```

### Parameters

| Name  | Data Type     | Description             |
| ----- | ------------- | ----------------------- |
| `ped` | ped (integer) | The target ped's handle |

## Example

```lua
RegisterNetEvent('drugs_creator:framework:ready', function()
    local closestPed = ESX.Game.GetClosestPed()

    exports["drugs_creator"]:removePedFromNPCSellingBlacklist(closestPed)
end)
```
