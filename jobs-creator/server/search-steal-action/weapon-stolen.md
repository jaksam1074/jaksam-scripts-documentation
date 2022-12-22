---
description: >-
  Triggered after a player steals something from the actions menu, only if you
  use the default player search/rob, it won't work if you replaced it
---

# Weapon stolen

```lua
RegisterNetEvent("jobs_creator:actions:weaponStolen", function(playerId, targetId, weaponName)

end)
```

#### Parameters

| Name         | Data Type | Description                                      |
| ------------ | --------- | ------------------------------------------------ |
| `playerId`   | integer   | The server ID of the player who stole the weapon |
| `targetId`   | integer   | The server ID of the victim who lost the weapon  |
| `weaponName` | string    | Weapon name                                      |

### Example

<pre class="language-lua"><code class="lang-lua"><strong>-- This example for ESX will "delete" the stolen weapons (maybe useful for cops)
</strong>RegisterNetEvent("jobs_creator:actions:weaponStolen", function(playerId, targetId, weaponName)
    local xPlayer = ESX.GetPlayerFromId(playerId)
    xPlayer.removeWeapon(weaponName)
end)
</code></pre>
