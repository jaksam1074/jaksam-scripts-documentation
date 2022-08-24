# Item harvested

Triggered after an harvestable item has been harvested

## Event

```lua
RegisterNetEvent("advanced_drugs_creator:harvest:itemHarvested", function(playerId, itemName, itemQuantity)

end)
```

### Parameters

| Name           | Data Type | Description             |
| -------------- | --------- | ----------------------- |
| `playerId`     | int       | Player server ID        |
| `itemName`     | string    | Item ID just harvested  |
| `itemQuantity` | int       | Item quantity harvested |

## Example

```lua
-- An example for a xp system
RegisterNetEvent("advanced_drugs_creator:harvest:itemHarvested", function(playerId, itemName, itemQuantity)
    TriggerEvent("xp_system:addXp", playerId, itemQuantity)
end)
```
