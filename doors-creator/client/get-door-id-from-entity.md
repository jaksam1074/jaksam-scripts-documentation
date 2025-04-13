# Get door ID from entity

## Export

```lua
exports["doors_creator"]:getDoorIdFromEntity(entity)
```

### Parameters

| Name     | Data Type | Description                            |
| -------- | --------- | -------------------------------------- |
| `entity` | integer   | The entity handle to get the door ID from |

### Returns

| Data Type | Description                                |
| --------- | ------------------------------------------ |
| integer   | The door ID if found, nil otherwise        |

## Example

```lua
-- This example shows how to add a target option to check door IDs using ox_target
-- Note: This is just an example, you'll need to adapt it to your needs and target system
Citizen.CreateThread(function() 
    exports.ox_target:addGlobalObject({
        {
            name = 'check_door_id',
            icon = 'fas fa-door-open',
            label = 'Check Door ID',
            onSelect = function(data)
                local doorId = exports["doors_creator"]:getDoorIdFromEntity(data.entity)
                
                if doorId then
                    print("Found door with ID: " .. doorId)
                end
            end
        }
    })
end)
``` 