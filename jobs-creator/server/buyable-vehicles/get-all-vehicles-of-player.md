# Get all vehicles of player

To get all vehicles owned by a player ID in all buyable garages

## Export

```lua
exports["jobs_creator"]:getAllVehiclesOfPlayer(playerId)
```

### Parameters

| Name       | Data Type | Description        |
| ---------- | --------- | ------------------ |
| `playerId` | integer   | Player's server ID |

### Return value

| Name       | Data Type | Description                                                                                                         |
| ---------- | --------- | ------------------------------------------------------------------------------------------------------------------- |
| `vehicles` | table     | Table with all vehicles owned by the player in the buyable garages, key is vehicle ID and value is the vehicle data |

## Example

```lua
local playerId = 4
local vehicles = exports["jobs_creator"]:getAllVehiclesOfPlayer(playerId)

print("Player vehicles:")
print(ESX.DumpTable(vehicles))
```
