# Delete door

## Export

```lua
exports["doors_creator"]:deleteDoor(doorId)
```

### Parameters

| Name     | Data Type | Description                   |
| -------- | --------- | ----------------------------- |
| `doorId` | integer   | The ID of the door to remove  |

### Returns

| Data Type | Description                                      |
| --------- | ------------------------------------------------ |
| boolean   | True if the door was removed, false otherwise    |

## Example

```lua
Citizen.CreateThread(function() 
    local doorId = 55
    
    local success = exports["doors_creator"]:deleteDoor(doorId)
    
    if success then
        print("Door with ID " .. doorId .. " has been removed")
    else
        print("Failed to remove door with ID " .. doorId)
    end
end)
``` 