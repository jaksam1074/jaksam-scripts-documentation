# Toggle icon display

Toggles icons/text of all doors

## Export

```lua
exports["doors_creator"]:toggleIconDisplay(newState)
```

### Return

| Name       | Data Type | Description                                                  |
| ---------- | --------- | ------------------------------------------------------------ |
| `newState` | bool      | <p>true = display icon/text<br>false = hide icon/display</p> |

## Example

```lua
RegisterCommand("hideDoorsIcon", function()
    exports["doors_creator"]:toggleIconDisplay(false)
end)
```
