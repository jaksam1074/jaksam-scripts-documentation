# Get all doors list

## Export

```lua
exports["doors_creator"]:getAllDoors()
```

### Return

A table with all doors data

## Example

```lua
Citizen.CreateThread(function() 
    local doors = exports["doors_creator"]:getAllDoors()

    for k, doorData in pairs(doors) do
        if(doorData.allowedJobs and doorData.allowedJob["police"]) then
            print(doorData.id .. " is a police door")
        end
    end
end)
```
