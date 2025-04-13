# Update door

## Export

```lua
exports["doors_creator"]:updateDoor(doorId, doorData)
```

### Parameters

| Name       | Data Type | Description                                    |
| ---------- | --------- | ---------------------------------------------- |
| `doorId`   | integer   | The ID of the door to update                   |
| `doorData` | table     | The door data to update with                   |

### doorData Format

This parameter can contain any of the fields used in AddDoor. You can provide only the fields you want to update, as the function will preserve existing values for fields not specified.

| Field                  | Data Type | Description                                            |
| ---------------------- | --------- | ------------------------------------------------------ |
| `label`                | string    | Name of the door                                       |
| `defaultState`         | integer   | Default state: 1 = locked, 0 = unlocked               |
| `doors`                | table     | Array of door objects with model and coordinates       |
| `maxDistance`          | number    | Maximum distance for interaction                       |
| `iconCoords`           | table     | Coordinates where to show the interaction icon         |
| `allowedJobs`          | table     | Table of jobs allowed to access, with grades           |
| `allowedGangs`         | table     | Table of gangs allowed to access, with grades          |
| `requiredItem`         | string    | Item required to access                                |
| `requiresJobAndItem`   | boolean   | If true, both job and item are required                |
| `requiredCode`         | string    | Code required to access                                |
| `autoClosureSeconds`   | integer   | Seconds after which doors auto-close                   |
| `parentBuilding`       | integer   | Building ID this door belongs to                       |
| `isSliding`            | boolean   | If true, door is sliding rather than hinged            |
| `displayIcon`          | boolean   | Whether to display interaction icon                    |
| `requiresIdentifier`   | boolean   | If true, specific identifiers are allowed              |
| `allowedIdentifiers`   | table     | Table of identifiers allowed to access                 |
| `vault`                | table     | Vault door configuration                               |
| `canBeLockpicked`      | boolean   | If true, door can be lockpicked                        |
| `alertPoliceOnLockpick`| boolean   | If true, police is alerted when door is lockpicked     |
| `soundsData`           | table     | Custom sounds configuration                            |
| `requiredItemRemoveOnUse` | boolean | If true, the required item will be removed on use     |

### Returns

| Data Type | Description                                      |
| --------- | ------------------------------------------------ |
| boolean   | True if the door was updated, false otherwise    |

## Example

```lua
Citizen.CreateThread(function() 
    local doorId = 55
    
    -- Example 1: Update only specific properties
    local doorData = {
        -- Update access permissions
        allowedIdentifiers = {
            ["steam:1100001xxxxxxxx"] = true,
            ["license:xxxxxxxxxxxxxxx"] = true
        },
        allowedJobs = {
            ["police"] = {
                ["0"] = true,
                ["1"] = true,
                ["2"] = true
            }
        },
        
        -- Update required item
        requiredItem = "special_key",
        
        -- Change lockpick settings
        canBeLockpicked = true,
        alertPoliceOnLockpick = true
    }
    
    local success = exports["doors_creator"]:updateDoor(doorId, doorData)
    
    if success then
        print("Door with ID " .. doorId .. " has been updated")
    else
        print("Failed to update door with ID " .. doorId)
    end
    
    -- Example 2: Complete door update
    -- This would replace all properties of the door
    local completeUpdate = {
        label = "Updated Door",
        defaultState = 0, -- Now unlocked by default
        doors = {
            {
                model = 747286790,
                coords = {
                    x = 152.7808,
                    y = -1000.5450,
                    z = 29.3962
                }
            }
        },
        maxDistance = 3.0, -- Increased interaction distance
        iconCoords = {
            x = 152.7808,
            y = -1000.5450,
            z = 29.3962
        },
        displayIcon = true,
        isSliding = false,
        parentBuilding = 2, -- Changed building association
        requiresJobAndItem = false
    }
    
    -- exports["doors_creator"]:updateDoor(doorId, completeUpdate)
end) 