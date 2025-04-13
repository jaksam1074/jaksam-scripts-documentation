# Create building

## Export
```lua
exports["doors_creator"]:createBuilding(buildingData)
```

### Parameters

| Name           | Data Type | Description                   |
| -------------- | --------- | ----------------------------- |
| `buildingData` | table     | The building data to be added |

### buildingData Format

| Field                  | Data Type | Description                                            | Required |
| ---------------------- | --------- | ------------------------------------------------------ | -------- |
| `label`                | string    | Name of the building                                   | Yes      |
| `defaultState`         | integer   | Default state: 1 = locked, 0 = unlocked               | Yes      |
| `allowedJobs`          | table     | Table of jobs allowed to access, with grades           | No       |
| `allowedGangs`         | table     | Table of gangs allowed to access, with grades          | No       |
| `requiredItem`         | string    | Item required to access                                | No       |
| `requiresJobAndItem`   | boolean   | If true, both job and item are required                | No       |
| `requiredCode`         | string    | Code required to access                                | No       |
| `autoClosureSeconds`   | integer   | Seconds after which doors auto-close                   | No       |
| `requiresIdentifier`   | boolean   | If true, specific identifiers are allowed              | No       |
| `allowedIdentifiers`   | table     | Table of identifiers allowed to access                 | No       |
| `requiredItemRemoveOnUse` | boolean | If true, the required item will be removed on use     | No       |

### Returns

| Data Type | Description                                       |
| --------- | ------------------------------------------------- |
| integer   | The building ID if successful, false otherwise    |

## Example

```lua
Citizen.CreateThread(function() 
    local buildingData = {
        label = "Police Department",
        defaultState = 1, -- 1 = locked, 0 = unlocked
        
        -- Jobs that can access this building
        allowedJobs = {
            ["police"] = {
                ["0"] = true, -- Recruit
                ["1"] = true, -- Officer
                ["2"] = true, -- Sergeant
                ["3"] = true  -- Lieutenant
            },
            ["sheriff"] = true
        },
        
        -- Gangs that can access (QB-Core only)
        allowedGangs = {
            ["ballas"] = {
                ["3"] = true -- Only boss rank
            }
        },
        
        -- Item required to access
        requiredItem = "police_keycard",
        
        -- If true, player needs both the job AND the item
        requiresJobAndItem = true,
        
        -- Keypad code (if applicable)
        requiredCode = "1234",
        
        -- Doors will auto-close after this many seconds
        autoClosureSeconds = 5,
        
        -- Individual player identifiers that can access
        requiresIdentifier = true,
        allowedIdentifiers = {
            ["153vav3xxxxxxxxxxxxxxx"] = true,
            ["6ba2f3xxxxxxxxxxxxxxxx"] = true
        },
        
        -- Remove the key item when used
        requiredItemRemoveOnUse = false
    }
    
    local buildingId = exports["doors_creator"]:createBuilding(buildingData)
    
    if buildingId then
        print("Building created with ID: " .. buildingId)
    else
        print("Failed to create building")
    end
end)
``` 
