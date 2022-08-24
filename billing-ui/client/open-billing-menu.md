# Open billing menu

Trigger to open the billing UI menu without making the player to select the target player with the mouse

## Event

```lua
TriggerEvent("billing_ui:openBillingMenu", targetServerID)
```

### Parameters

| Name             | Data Type | Description             |
| ---------------- | --------- | ----------------------- |
| `targetServerID` | integer   | Target server ID or nil |

## Example

```lua
local closestPlayer = ESX.Game.GetClosestPlayer()
local targetPlayerId = GetPlayerServerId(closestPlayer)

TriggerEvent("billing_ui:openBillingMenu", targetPlayerId)
```
