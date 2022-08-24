# Manually sell to a NPC

Trigger to start selling to an NPC, as you would do after pressing E to sell in the default method

## Event

```lua
TriggerEvent("advanced_drugs_creator:sellToNPC", ped)
```

### Parameters

| Name  | Data Type     | Description             |
| ----- | ------------- | ----------------------- |
| `ped` | ped (integer) | The target ped's handle |

## Example

```lua
local closestPed = ESX.Game.GetClosestPed()

TriggerEvent("advanced_drugs_creator:sellToNPC", closestPed)
```
