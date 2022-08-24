# Get door ID data

## Export

```lua
exports["doors_creator"]:getDoorIdData(doorId)
```

### Parameters

| Name     | Data Type | Description                 |
| -------- | --------- | --------------------------- |
| `doorId` | integer   | The door ID to get the data |

## Example

```lua
Citizen.CreateThread(function() 
    local doorId = 55
    local doorData = exports["doors_creator"]:getDoorIdData(doorId)

    print("The name of the door " .. doorId .. " is " .. doorData.label)
end)
```
