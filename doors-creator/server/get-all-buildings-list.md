# Get all buildings list

## Export

```lua
exports["doors_creator"]:getAllBuildings()
```

### Return

A table with all buildings data

## Example

```lua
Citizen.CreateThread(function() 
    local buildings = exports["doors_creator"]:getAllBuildings()

    for k, buildingData in pairs(buildings) do            
        if(buildingData.allowedJobs and buildingData.allowedJobs["police"]) then
            print(buildingData.label .. " is a police building")
        end
    end
end)
```
