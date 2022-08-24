# Step completed

Triggered when a step of a heist is completed

## Event

```lua
RegisterNetEvent("robberies_creator:heist:stepCompleted", function(playerId, heistId, stageId, stepType)

end)
```

### Parameters

| Name       | Data Type | Description                                                                           |
| ---------- | --------- | ------------------------------------------------------------------------------------- |
| `playerId` | int       | player server ID who completed the step                                               |
| `heistId`  | int       | Heist ID                                                                              |
| `stageId`  | int       | Stage ID                                                                              |
| `stepType` | string    | The step type. Available steps types are defined [here](step-completed.md#step-types) |

### Step types

* `SAFE`
* `ROBBABLE_OBJECT`
* `HACKABLE_PANEL`
* `THERMAL_CHARGE`
* `LOCKPICKABLE_DOOR`

## Example

```lua
-- This hypothetical example will give xp when a player does a step which has a minigame
RegisterNetEvent("robberies_creator:heist:stepCompleted", function(playerId, heistId, stageId, stepType)
    if(stepType ~= "ROBBABLE_OBJECT") then
        TriggerEvent("xp_script:addPlayerXp", playerId, 10)
    end
end)
```

## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
