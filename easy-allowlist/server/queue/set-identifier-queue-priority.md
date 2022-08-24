# Set identifier queue priority

To set an identifier queue priority

## Export

```lua
exports["easy_allowlist"]:setIdentifierQueuePriority(identifier, priority)
```

### Parameters

| Name         | Data Type | Description              |
| ------------ | --------- | ------------------------ |
| `identifier` | string    | Player's main identifier |
| `priority`   | integer   | Queue priority           |

## Example

```lua
exports["easy_allowlist"]:setIdentifierQueuePriority("steam:71002010c2f9c5d", 15)
```
