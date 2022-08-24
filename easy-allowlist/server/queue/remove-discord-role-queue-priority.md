# Remove discord role queue priority

To remove a queue priority for a Discord Role

## Export

```lua
exports["easy_allowlist"]:removeDiscordRoleQueuePriority(identifier)
```

### Parameters

| Name         | Data Type | Description                |
| ------------ | --------- | -------------------------- |
| `identifier` | string    | The player main identifier |

## Example

```lua
local discordRoleId = "332962646660794880"
exports["easy_allowlist"]:removeDiscordRoleQueuePriority(discordRoleId)
```
