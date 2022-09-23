# Set handcuffs state

To set the handcuffs state of a player, without the animation

## Export

```lua
exports["jobs_creator"]:setHandcuffs(playerId, state)
```

### Parameters

| Name     | Data type | Description                     |
| -------- | --------- | ------------------------------- |
| playerId | integer   | The target player server ID     |
| state    | boolean   | true = handcuffed, false = free |

## Example

```lua
-- This is just an example and won't work, require you to use the export properly
RegisterNetEvent("hospital_script:playerDead", function(playerId)
    -- The script code
    -- The script code
    -- The script code
    
    -- The dead player is not handcuffed anymore
    exports["jobs_creator"]:setHandcuffs(playerId, false)
end)
```
