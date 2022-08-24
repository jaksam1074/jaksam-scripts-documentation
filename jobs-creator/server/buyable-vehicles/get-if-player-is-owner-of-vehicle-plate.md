# Get if player is owner of vehicle plate

Returns if a player ID is the owner of a specific plate

## Export

```lua
exports["jobs_creator"]:isPlayerOwnerOfVehiclePlate(playerId, plate)
```

### Parameters

| Name       | Data Type | Description        |
| ---------- | --------- | ------------------ |
| `playerId` | integer   | Player's server ID |
| `plate`    | string    | Vehicle's plate    |

### Return value

| Name      | Data Type | Description                               |
| --------- | --------- | ----------------------------------------- |
| `isOwner` | bool      | If the player is the vehicle owner or not |

## Example

```lua
local playerId = 1
local plate = "40PQB261"
local isTheVehicleOwner = exports["jobs_creator"]:isPlayerOwnerOfVehiclePlate(playerId, plate)

print("Is the player owner of that plate: " .. tostring(isTheVehicleOwner))
```
