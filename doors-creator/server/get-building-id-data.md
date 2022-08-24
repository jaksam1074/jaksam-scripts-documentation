# Get building ID data

## Export

```lua
exports["doors_creator"]:getBuildingIdData(buildingId)
```

### Parameters

| Name         | Data Type | Description                     |
| ------------ | --------- | ------------------------------- |
| `buildingId` | integer   | The building ID to get the data |

## Example

```lua
Citizen.CreateThread(function() 
    local buildingId = 55
    local buildingData = exports["doors_creator"]:getBuildingIdData(buildingId)

    print("The name of the building " .. buildingId .. " is " .. buildingData.label)
end)
```
