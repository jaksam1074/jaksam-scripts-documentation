# Item crafted

Triggered when a player crafts an item in crafting table marker

### Event

```lua
RegisterNetEvent("jobs_creator:crafting_table:craftedItem", function(playerId, markerId, itemName, itemQuantity)

end)
```

#### Parameters

| Name           | Data Type | Description           |
| -------------- | --------- | --------------------- |
| `playerId`     | integer   | Player's server ID    |
| `markerId`     | integer   | Marker ID             |
| `itemName`     | integer   | Crafted item name     |
| `itemQuantity` | integer   | Crafted item quantity |

### Example

```lua
RegisterNetEvent("jobs_creator:crafting_table:craftedItem", function(playerId, markerId, itemName, itemQuantity)
    TriggerEvent("xp_system:addExperience", playerId, "craft")
end)
```
