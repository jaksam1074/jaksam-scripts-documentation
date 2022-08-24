# Get player ID keys

## Export

```lua
exports["vehicles_keys"]:getPlayerIdKeys(playerId)
```

### Parameters

| Name       | Data Type | Description                 |
| ---------- | --------- | --------------------------- |
| `playerId` | integer   | The target player server ID |

## Example

```lua
Citizen.CreateThread(function() 
    local playerServerId = 16

    local keys = exports["vehicles_keys"]:getPlayerIdKeys(playerServerId)

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
