# Set discord role queue priority

To set a queue priority for a Discord Role ID

## Export

```lua
exports["easy_allowlist"]:setDiscordRolePriority(discordRoleId, priority)
```

### Parameters

| Name            | Data Type | Description     |
| --------------- | --------- | --------------- |
| `discordRoleId` | integer   | Discord role ID |
| `priority`      | integer   | Queue priority  |

## Example

```lua
local discordRoleId = "332962646660794880"
exports["easy_allowlist"]:setDiscordRolePriority(discordRoleId, 30)
```
