# Create door

## Export

```lua
exports["doors_creator"]:createDoor(doorData)
```

### Parameters

| Name       | Data Type | Description                  |
| ---------- | --------- | ---------------------------- |
| `doorData` | table     | The door data to be added    |

### doorData Format

| Field                  | Data Type | Description                                            | Required |
| ---------------------- | --------- | ------------------------------------------------------ | -------- |
| `label`                | string    | Name of the door                                       | Yes      |
| `defaultState`         | integer   | Default state: 1 = locked, 0 = unlocked               | Yes      |
| `doors`                | table     | Array of door objects with model and coordinates       | Yes      |
| `maxDistance`          | number    | Maximum distance for interaction                       | Yes      |
| `iconCoords`           | table     | Coordinates where to show the interaction icon         | Yes      |
| `allowedJobs`          | table     | Table of jobs allowed to access, with grades           | No       |
| `allowedGangs`         | table     | Table of gangs allowed to access, with grades          | No       |
| `requiredItem`         | string    | Item required to access                                | No       |
| `requiresJobAndItem`   | boolean   | If true, both job and item are required                | No       |
| `requiredCode`         | string    | Code required to access                                | No       |
| `autoClosureSeconds`   | integer   | Seconds after which doors auto-close                   | No       |
| `parentBuilding`       | integer   | Building ID this door belongs to                       | No       |
| `isSliding`            | boolean   | If true, door is sliding rather than hinged            | No       |
| `displayIcon`          | boolean   | Whether to display interaction icon                    | No       |
| `requiresIdentifier`   | boolean   | If true, specific identifiers are allowed              | No       |
| `allowedIdentifiers`   | table     | Table of identifiers allowed to access                 | No       |
| `vault`                | table     | Vault door configuration                               | No       |
| `canBeLockpicked`      | boolean   | If true, door can be lockpicked                        | No       |
| `alertPoliceOnLockpick`| boolean   | If true, police is alerted when door is lockpicked     | No       |
| `soundsData`           | table     | Custom sounds configuration                            | No       |
| `requiredItemRemoveOnUse` | boolean | If true, the required item will be removed on use     | No       |

### Returns

| Data Type | Description                                    |
| --------- | ---------------------------------------------- |
| boolean   | True if the door was added, false otherwise    |

## Example

```lua
Citizen.CreateThread(function() 
    local doorData = {
        label = "Police Front Door",
        defaultState = 1, -- 1 = locked, 0 = unlocked
        
        -- Array of physical doors objects
        doors = {
            {
                model = 747286790, -- Hash of the door model
                coords = {
                    x = 152.7808,
                    y = -1000.5450,
                    z = 29.3962
                }
            },
            -- You can add a second door for double doors
            {
                model = 747286791,
                coords = {
                    x = 154.8200,
                    y = -1000.5450,
                    z = 29.3962
                }
            }
        },
        
        -- Maximum distance for interaction
        maxDistance = 2.0,
        
        -- Where to show the interaction icon
        iconCoords = {
            x = 153.7808,
            y = -1000.5450,
            z = 29.3962
        },
        
        -- Jobs that can access this door
        allowedJobs = {
            ["police"] = {
                ["0"] = true, -- Recruit
                ["1"] = true, -- Officer
                ["2"] = true  -- Sergeant
            },

            ["ambulance"] = true
        },
        
        -- Gangs that can access (QB-Core only)
        allowedGangs = {
            ["ballas"] = {
                ["2"] = true, -- Only higher ranks
                ["3"] = true
            }
        },
        
        -- Item required to access
        requiredItem = "police_keycard",
        
        -- If true, player needs both the job AND the item
        requiresJobAndItem = false,
        
        -- Building this door belongs to
        parentBuilding = 1,
        
        -- If it's a sliding door
        isSliding = false,
        
        -- Whether to display interaction icon
        displayIcon = true,
        
        -- Door can be lockpicked
        canBeLockpicked = true,
        
        -- Alert police when lockpicked
        alertPoliceOnLockpick = true,
        
        -- Custom sounds
        soundsData = {
            lockSound = "fence",
            unlockSound = "fence"
        }
    }
    
    local success = exports["doors_creator"]:createDoor(doorData)
    
    if success then
        print("Door created successfully")
    else
        print("Failed to create door")
    end
end)
``` 