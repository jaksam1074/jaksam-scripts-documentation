# Get count of players currently in queue

Use the following export if you need to get **the count of players currently in queue**

## Export
```lua
-- Returns a number
exports["easy_allowlist"]:getQueueCount()
```

## Example

```lua
RegisterCommand("queuecount", function(source, args)
    local queueCount = exports["easy_allowlist"]:getQueueCount()
    print("Queue count: " .. queueCount)
end, false)
```

__You can add this code in sv_integrations.lua of the script or in any other server side lua file__