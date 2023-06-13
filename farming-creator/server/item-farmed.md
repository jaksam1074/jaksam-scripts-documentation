# Item farmed

This page will have events that are triggered **after** a player farms anywhere



### Farms

```lua
RegisterNetEvent("farming_creator:farms:completed", function(playerId, farmId, givenItems)
    -- An example for a xp system
    TriggerEvent("xp_system:addXp", playerId)
end)
```

### Fields

```lua
RegisterNetEvent("farming_creator:fields:completed", function(playerId, fieldId, givenItems)
    -- An example for a xp system
    TriggerEvent("xp_system:addXp", playerId)
end)
```

### Foundries

```lua
RegisterNetEvent("farming_creator:foundries:completed", function(playerId, foundryId, givenItems)
    -- An example for a xp system
    TriggerEvent("xp_system:addXp", playerId)
end)
```

### Seeds

```lua
RegisterNetEvent("farming_creator:seeds:interacted", function(playerId, seedId, givenItems)
    -- An example for a xp system
    TriggerEvent("xp_system:addXp", playerId)
end)
```

### Workbenches

```lua
RegisterNetEvent("farming_creator:workbenches:completed", function(playerId, workbenchId, givenItems)
    -- An example for a xp system
    TriggerEvent("xp_system:addXp", playerId)
end)
```
