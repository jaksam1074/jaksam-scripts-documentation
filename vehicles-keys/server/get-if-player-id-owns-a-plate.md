# Get if player ID owns a plate

This export can be used to know if **the local player** owns a vehicle plate

## Export

```lua
exports["vehicles_keys"]:isPlayerOwnerOfVehiclePlate(playerId, plate, onlyOwnedVehicles)
```

### Parameters

| Name                | Data Type | Description                                                                                                      |
| ------------------- | --------- | ---------------------------------------------------------------------------------------------------------------- |
| `playerId`          | integer   | The player server ID                                                                                             |
| `plate`             | string    | The vehicle plate to check                                                                                       |
| `onlyOwnedVehicles` | boolean   | <p>true = only searches for owned vehicles<br>false = allows to search temporary vehicles, shared keys, etc.</p> |

### Return

`true` if the vehicle is owned

`false` if the vehicle is not owned

## Example

```lua
RegisterCommand("checkPlate", function(playerId, args)
    local plate = args[1] -- Example "ABC 123"
    
    if(exports["vehicles_keys"]:isPlayerOwnerOfVehiclePlate(playerId, plate, false)) then
        print("I own this vehicle plate")
    else
        print("I DO NOT own this vehicle plate")
    end
end)
```
