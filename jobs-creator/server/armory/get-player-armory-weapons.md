# Get player armory weapons

To get a list of weapons of a player stored in a specific armory ID.

### Export

```lua
exports["jobs_creator"]:getPlayerArmoryWeapons(playerId, markerId)
```

#### Parameters

| Name       | Data Type | Description      |
| ---------- | --------- | ---------------- |
| `playerId` | integer   | Player server ID |
| `markerId` | integer   | The marker ID    |

#### Return value

| Name                  | Data Type | Description                                                         |
| --------------------- | --------- | ------------------------------------------------------------------- |
| `playerArmoryWeapons` | table     | List of all weapons contained in the marker deposited by the player |

### Example

```lua
local playerId = 20
local markerId = 52

local playerArmoryWeapons = getPlayerArmoryWeapons(playerId, markerId)

print("Player weapons in that armory")
print(ESX.DumpTable(playerArmoryWeapons))
```
