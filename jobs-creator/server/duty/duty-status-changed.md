# Duty status changed

Triggered after player goes on/off duty server side

### Event

```lua
RegisterNetEvent("jobs_creator:toggleDuty", function(playerId, jobName, isOnDuty)

end)
```

#### Parameters

| Name       | Data Type | Description             |
| ---------- | --------- | ----------------------- |
| `playerId` | integer   | Target player server ID |
| `jobName`  | string    | Player's job id         |
| `isOnDuty` | boolean   | Player new duty status  |

### Example

```lua
RegisterNetEvent("jobs_creator:toggleDuty", function(playerId, jobName, isOnDuty)
    if(isOnDuty) then
        TriggerEvent("external_scoreboard:increaseOnDutyCount", jobName)
    else
        TriggerEvent("external_scoreboard:decreaseOnDutyCount", jobName)
    end
end)
```
