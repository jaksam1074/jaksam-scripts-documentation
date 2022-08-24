# Get identifier keys

## Export

```lua
exports["vehicles_keys"]:getIdentifierKeys(identifier)
```

### Parameters

| Name         | Data Type | Description                          |
| ------------ | --------- | ------------------------------------ |
| `identifier` | string    | The target player identifier/license |

## Example

```lua
Citizen.CreateThread(function() 
    local identifier = "abcedfghj12356"

    local keys = exports["vehicles_keys"]:getIdentifierKeys(identifier)

    print(ESX.DumpTable(keys))

    --[[
        Example output

        {
            ["ABC123"] = {
                ["type"] = "owned",
                ["model"] = -563445643
            },

            ["VEG643"] = {
                ["type"] = "temporary",
                ["model"] = 165445642
            },

            ["AEC613"] = {
                ["type"] = "other_player",
                ["model"] = 1732123
            },
        }
    ]]

end)
```
