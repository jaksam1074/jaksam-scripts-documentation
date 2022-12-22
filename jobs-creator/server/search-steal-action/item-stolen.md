---
description: >-
  Triggered after a player steals something from the actions menu, only if you
  use the default player search/rob, it won't work if you replaced it
---

# Item stolen

```lua
RegisterNetEvent("jobs_creator:actions:itemStolen", function(playerId, targetId, itemName, itemQuantity)

end)
```

#### Parameters

| Name           | Data Type | Description                                    |
| -------------- | --------- | ---------------------------------------------- |
| `playerId`     | integer   | The server ID of the player who stole the item |
| `targetId`     | integer   | The server ID of the victim who lost the item  |
| `itemName`     | string    | Item name                                      |
| `itemQuantity` | integer   | Quantity stolen                                |

### Example

<pre class="language-lua"><code class="lang-lua"><strong>-- This example for ESX will "delete" all stolen items
</strong><strong>RegisterNetEvent("jobs_creator:actions:itemStolen", function(playerId, targetId, itemName, itemQuantity)
</strong>    local xPlayer = ESX.GetPlayerFromId(playerId)
    xPlayer.removeInventoryItem(itemName, itemQuantity)
end)
</code></pre>
