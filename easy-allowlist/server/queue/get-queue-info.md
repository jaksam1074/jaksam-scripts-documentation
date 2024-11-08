# Get queue info

Use the following export to get the data of the players who are currently in queue (nickname, identifier, priority, etc.)

## Export
```lua
-- Returns a table
exports["easy_allowlist"]:getPlayersInQueue()
```

## Example

```lua
RegisterCommand("queueinfo", function(source, args)
    local queueInfo = exports["easy_allowlist"]:getPlayersInQueue()
    print(json.encode(queueInfo, { indent = true }))
end, false)
```

__You can add this code in sv_integrations.lua of the script or in any other server side lua file__