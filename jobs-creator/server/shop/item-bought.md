# Item bought

Triggered when a player buys an item/weapon in shop marker

### Event

```lua
RegisterNetEvent("jobs_creator:shop:boughtItem", function(playerId, markerId, itemName, itemQuantity, totalPrice)

end)
```

#### Parameters

| Name           | Data Type | Description              |
| -------------- | --------- | ------------------------ |
| `playerId`     | integer   | Player's server ID       |
| `markerId`     | integer   | Marker ID                |
| `itemName`     | string    | Item name or weapon name |
| `itemQuantity` | integer   | Bought quantity          |
| `totalPrice`   | integer   | Total paid price         |

### Example

```lua
RegisterNetEvent("jobs_creator:shop:boughtItem", function(playerId, markerId, itemName, itemQuantity, totalPrice)
    print("Player ID :" .. playerId .. " bought x" .. itemQuantity .. " " .. itemName .. " from shop " .. markerId)
end)
```
