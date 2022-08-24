# Manually start drugs effects

Trigger to start drug effects (you may prefer to trigger this from server side)

## Event

```lua
TriggerEvent("advanced_drugs_creator:drugEffects", takingMethod, effects, effectsDuration)
```

### Parameters

| Name              | Data Type | Description                                                |
| ----------------- | --------- | ---------------------------------------------------------- |
| `takingMethod`    | string    | How the player will take the drug                          |
| `effects`         | table     | An array of strings containing all effects you want to add |
| `effectsDuration` | integer   | Seconds the effects will last                              |

### Taking methods

`"pill"`\
`"drink"`\
`"smoke"`\
`"needle"`\


### Effects

`"visual_shaking"`\
`"drunk_walk"`\
`"fall"`\
`"pink_visual"`\
`"green_visual"`\
`"confused_visual"`\
`"armor50"`\
`"armor100"`\
`"health50"`\
`"health100"`\
`"sprint_faster"`\
`"swim_faster"`\
`"infinite_stamina"`\


## Example - Client side

```lua
RegisterCommand("effects", function() 
    local takingMethod = "pill"
    local effects = {
        "drunk_walk",
        "swim_faster",
        "green_visual",
    }

    local effectsDuration = 120 -- seconds

    TriggerEvent("advanced_drugs_creator:drugEffects", takingMethod, effects, effectsDuration)
end)
```

## Example - Server side

```lua
RegisterCommand("effects", function(playerId) 
    local takingMethod = "pill"
    local effects = {
        "drunk_walk",
        "swim_faster",
        "green_visual",
    }

    local effectsDuration = 120 -- seconds

    TriggerClientEvent("advanced_drugs_creator:drugEffects", playerId, takingMethod, effects, effectsDuration)
end)
```
