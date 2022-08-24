# Vehicle locked/unlocked

Triggered when the vehicle lock has been toggled

## Event

```lua
RegisterNetEvent("vehicles_keys:vehicleLockChanged", function(vehicle, isLocked)

end)
```

### Parameters

| Name       | Data Type | Description                         |
| ---------- | --------- | ----------------------------------- |
| `vehicle`  | int       | Vehicle handle                      |
| `isLocked` | bool      | If now the vehicle is locked or not |

## Example

```lua
RegisterNetEvent("vehicles_keys:vehicleLockChanged", function(vehicle, isLocked)
    print("The vehicle " .. vehicle .. " is now " .. (isLocked and "locked" or "unlocked"))
end)
```

## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
