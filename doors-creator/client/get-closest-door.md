# Get closest door

Returns the closest **active** door to the player

## Export

```lua
exports["doors_creator"]:getClosestActiveDoor()
```

### Return

| Name       | Data Type | Description                                      |
| ---------- | --------- | ------------------------------------------------ |
| `door`     | table     | Table containing the door.id and the door.object |
| `distance` | float     | Distance from the door                           |

## Example

```lua
Citizen.CreateThread(function() 
    local closestDoor, closestDist = exports["doors_creator"]:getClosestActiveDoor()

    if(closestDoor and closestDist < 3.0) then
        print("The closest door is " .. closestDoor.id .. " and is " .. closestDist .. " meters away")
    end
end)
```
