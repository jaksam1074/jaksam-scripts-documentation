# Toggle hotwiring

This export can be useful when you want the player to not be able to use the hotwiring anymore **temporary**

## Export

```lua
exports["vehicles_keys"]:toggleHotwiring(newState)
```

### Parameters

| Name       | Data Type | Description                                               |
| ---------- | --------- | --------------------------------------------------------- |
| `newState` | bool      | `true` = hotwiring enabled - `false` = hotwiring disabled |

## Example

```lua
RegisterNetEvent("vehicle_shop:enteredList", function() 
    exports["vehicles_keys"]:toggleHotwiring(false)
end)

RegisterNetEvent("vehicle_shop:exitedList", function() 
    exports["vehicles_keys"]:toggleHotwiring(true)
end)
```
