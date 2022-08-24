# Set player queue priority

To set a queue priority to an online player ID

## Export

```lua
exports["easy_allowlist"]:setPlayerQueuePriority(playerId, priority)
```

### Parameters

| Name       | Data Type | Description      |
| ---------- | --------- | ---------------- |
| `playerId` | integer   | Player server ID |
| `priority` | integer   | Queue priority   |

## Example

```lua
local playerId = 61
exports["easy_allowlist"]:setPlayerQueuePriority(playerId, 15)
```
