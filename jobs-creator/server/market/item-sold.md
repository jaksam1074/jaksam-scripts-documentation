# Item sold

Triggered when a player buys an item/weapon in shop marker

### Event

```lua
RegisterNetEvent("jobs_creator:market:soldItem", function(playerId, markerId, itemName, itemQuantity, totalPrice)

end)
```

#### Parameters

| Name           | Data Type | Description              |
| -------------- | --------- | ------------------------ |
| `playerId`     | integer   | Player's server ID       |
| `markerId`     | integer   | Marker ID                |
| `itemName`     | string    | Item name or weapon name |
| `itemQuantity` | integer   | Bought quantity          |
| `totalPrice`   | integer   | Total received money     |

### Example

```lua
RegisterNetEvent("jobs_creator:market:soldItem", function(playerId, markerId, itemName, itemQuantity, totalPrice)
    print("Player ID :" .. playerId .. " sold x" .. itemQuantity .. " " .. itemName .. " from shop " .. markerId)
end)
```
