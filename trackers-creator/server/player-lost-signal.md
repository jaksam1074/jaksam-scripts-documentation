# Player lost signal

This event is triggered when a player loses signal of a tracker, because he lost the required item

## Event

```lua
AddEventHandler("trackers_creator:playerPressedPanicButton", function(playerId, trackerId)

end)
```



### Parameters

| Name        | Data Type | Description                      |
| ----------- | --------- | -------------------------------- |
| `playerId`  | integer   | The server ID of the player      |
| `trackerId` | integer   | The tracker ID which lost signal |

## Example

```lua
RegisterNetEvent("trackers_creator:playerLostSignalWithTracker", function(playerId, trackerId)
    -- You can use any code there to retrieve data from the database or do anything
end)
```
