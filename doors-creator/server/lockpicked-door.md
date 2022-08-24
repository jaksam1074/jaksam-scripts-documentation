# Lockpicked door

## Event

```lua
RegisterNetEvent("doors_creator:doorHasBeenLockpicked", function(playerId, doorId)

end)
```

### Parameters

| Name       | Data Type | Description                                         |
| ---------- | --------- | --------------------------------------------------- |
| `playerId` | integer   | The server id of the player who lockpicked the door |
| `doorId`   | integer   | The door ID that has been lockpicked                |

## Example

```lua
RegisterNetEvent("doors_creator:doorHasBeenLockpicked", function(playerId, doorId)
    local playerName = GetPlayerName(playerId)

    local doorData = exports["doors_creator"]:getDoorIdData(doorId)

    local doorCoords = doorData.coords

    for k, playerId in pairs(GetPlayers()) do
        local xPlayer = ESX.GetPlayerFromId(playerId)

        if(xPlayer.job.name == "police") then
            TriggerClientEvent("alert_system:alert", playerId, doorCoords, "Door has been lockpicked")
        end
    end
end)
```
