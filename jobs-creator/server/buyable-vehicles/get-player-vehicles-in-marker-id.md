# Get player vehicles in marker ID

To get all vehicles owned by a player ID in a specific buyable garage marker ID

## Export

```lua
exports["jobs_creator"]:getPlayerVehiclesInMarkerId(playerId, markerId)
```

### Parameters

| Name       | Data Type | Description        |
| ---------- | --------- | ------------------ |
| `playerId` | integer   | Player's server ID |
| `markerId` | integer   | Marker ID          |

### Return value

| Name       | Data Type | Description                                                                                                |
| ---------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `vehicles` | table     | Table with all vehicles owned by the player in the garage, key is vehicle ID and value is the vehicle data |

## Example

```lua
local playerId = 1
local markerId = 252
local playerVehiclesInMarker = exports["jobs_creator"]:getPlayerVehiclesInMarkerId(playerId, markerId)

print(ESX.DumpTable(playerVehiclesInMarker))
```
