# Player set new private frequency

This event is triggered when a player uses the private tracker item and sets a new frequency

## Event

```lua
AddEventHandler("trackers_creator:playerSetNewPrivateFrequency", function(playerId, trackerId)

end)
```

### Parameters

| Name        | Data Type | Description                  |
| ----------- | --------- | ---------------------------- |
| `playerId`  | integer   | The server ID of the player  |
| `frequency` | integer   | New frequency choosen        |
