# Item processed

Triggered when a player processes an item in process marker

### Event

```lua
RegisterNetEvent("jobs_creator:process:processedItem", function(playerId, markerId, addedItemName, addedItemQuantity, removedItemName, removedItemQuantity)

end)
```

#### Parameters

| Name                  | Data Type | Description            |
| --------------------- | --------- | ---------------------- |
| `playerId`            | integer   | Player's server ID     |
| `markerId`            | integer   | Marker ID              |
| `addedItemName`       | string    | Received item name     |
| `addedItemQuantity`   | integer   | Received item quantity |
| `removedItemName`     | integer   | Removed item name      |
| `removedItemQuantity` | integer   | Removed item quantity  |

### Example

```lua
RegisterNetEvent("jobs_creator:process:processedItem", function(playerId, markerId, addedItemName, addedItemQuantity, removedItemName, removedItemQuantity)
    TriggerEvent("xp_system:addExperience", playerId, "process")
end)
```
