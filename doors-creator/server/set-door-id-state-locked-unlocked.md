# Set door ID state (locked/unlocked)

## Export

```lua
exports["doors_creator"]:setDoorState(doorId, state)
```

### Parameters

| Name     | Data Type | Description                              |
| -------- | --------- | ---------------------------------------- |
| `doorId` | integer   | The door ID                              |
| `state`  | integer   | Door new state. 1 = locked, 0 = unlocked |

## Example

```lua
Citizen.CreateThread(function() 
    local doors = exports["doors_creator"]:getAllDoors()

    -- This will close ALL the doors
    for k, doorData in pairs(doors) do
        exports["doors_creator"]:setDoorState(doorData.id, 1)
    end
end)
```
