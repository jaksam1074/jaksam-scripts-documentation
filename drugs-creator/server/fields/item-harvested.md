# Item harvested

Triggered after an item has been harvested in a field

## Event

```lua
RegisterNetEvent("advanced_drugs_creator:fields:itemHarvested", function(playerId, fieldId, itemName, itemQuantity)

end)
```

### Parameters

| Name           | Data Type | Description                           |
| -------------- | --------- | ------------------------------------- |
| `playerId`     | int       | Player server ID                      |
| `fieldId`      | int       | Field ID where the item was harvested |
| `itemName`     | string    | Item ID just harvested                |
| `itemQuantity` | int       | Item quantity harvested               |

## Example

```lua
-- An example for a xp system
RegisterNetEvent("advanced_drugs_creator:fields:itemHarvested", function(playerId, fieldId, itemName, itemQuantity)
    TriggerEvent("xp_system:addXp", playerId, itemName, itemQuantity)
end)
```
