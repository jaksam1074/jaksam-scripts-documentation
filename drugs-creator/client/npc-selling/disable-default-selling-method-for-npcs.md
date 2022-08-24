# Disable default selling method for NPCs

Trigger to disable the prompt above NPCs "Press E to sell drugs"\
\
If you disable the prompt, you have to manually trigger the `advanced_drugs_creator:sellToNPC` event to sell to NPCs

## Event

```lua
TriggerEvent("advanced_drugs_creator:disableDefaultSellingMethodNPC")
```

## Example

```lua
-- Disables the prompt
RegisterNetEvent("advanced_drugs_creator:framework:ready", function() 
    TriggerEvent("advanced_drugs_creator:disableDefaultSellingMethodNPC")
end)

-- Manually sell to an NPC (example for targeting scripts)
Citizen.CreateThread(function() 
    local closestPed = ESX.Game.GetClosestPed()

    TriggerEvent("advanced_drugs_creator:sellToNPC", closestPed)
end)
```
