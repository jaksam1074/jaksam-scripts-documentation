# Item harvested

Triggered when a player harvests an item in harvest marker

### Event

```lua
RegisterNetEvent("jobs_creator:harvest:harvestedItem", function(playerId, markerId, itemName, itemQuantity)

end)
```

#### Parameters

| Name           | Data Type | Description        |
| -------------- | --------- | ------------------ |
| `playerId`     | integer   | Player's server ID |
| `markerId`     | integer   | Marker ID          |
| `itemName`     | string    | Item name          |
| `itemQuantity` | integer   | Harvested quantity |

### Example

```lua
RegisterNetEvent("jobs_creator:harvest:harvestedItem", function(playerId, markerId, itemName, itemQuantity)
    print("Player ID :" .. playerId .. " harvested " .. itemQuantity .. " " .. itemName .. " from marker " .. markerId)

    TriggerEvent("xp_system:addExperience", playerId, "harvest")
end)
```
