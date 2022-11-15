# Toggle closest vehicle lock

This export can be used to manually toggle a vehicle lock

## Export

```lua
exports["vehicles_keys"]:toggleClosestVehicleLock()
```

## Example

```lua
RegisterCommand("togglelock", function(_, args)
    exports["vehicles_keys"]:toggleClosestVehicleLock()
end)
```
