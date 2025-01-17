# Get if local player owns a plate

This export can be used to know if **the local player** owns a vehicle plate. Will also check for shared, temporary, etc.

## Export

```lua
exports["vehicles_keys"]:doesPlayerOwnPlate(plate)
```

### Parameters

| Name    | Data Type | Description                |
| ------- | --------- | -------------------------- |
| `plate` | string    | The vehicle plate to check |

### Return

`true` if the vehicle is owned

`false` if the vehicle is not owned

## Example

```lua
RegisterCommand("checkPlate", function(_, args)
    local plate = args[1] -- Example "ABC 123"
    
    if(exports["vehicles_keys"]:doesPlayerOwnPlate(plate)) then
        print("I own this vehicle plate")
    else
        print("I DO NOT own this vehicle plate")
    end
end)
```
