---
description: >-
  Triggered after a player steals something from the actions menu, only if you
  use the default player search/rob, it won't work if you replaced it
---

# Account stolen

```lua
RegisterNetEvent("jobs_creator:actions:accountStolen", function(playerId, targetId, accountName, amount)

end)
```

#### Parameters

| Name          | Data Type | Description                                     |
| ------------- | --------- | ----------------------------------------------- |
| `playerId`    | integer   | The server ID of the player who stole the money |
| `targetId`    | integer   | The server ID of the victim who lost the money  |
| `accountName` | string    | Account name (example "bank")                   |
| `amount`      | integer   | Amount stolen                                   |

### Example

```lua
RegisterNetEvent("jobs_creator:actions:accountStolen", function(playerId, targetId, accountName, amount)
    print(GetPlayerName(playerId) .. " has stolen " .. amount .. " " .. accountName .. " from " .. GetPlayerName(targetId))
end)
```
