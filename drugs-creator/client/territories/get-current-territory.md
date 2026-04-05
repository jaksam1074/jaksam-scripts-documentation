# Get current territory

Returns the name of the territory the local player is currently inside, or `nil` if outside any territory

## Export

```lua
local territoryName = exports["drugs_creator"]:getCurrentTerritory()
```

### Returns

| Data Type    | Description                                             |
| ------------ | ------------------------------------------------------- |
| string / nil | The territory name, or nil if the player is not in one  |

## Example

```lua
local territory = exports["drugs_creator"]:getCurrentTerritory()

if territory then
    print("You are in territory: " .. territory)
else
    print("You are not inside any territory")
end
```
