# Send a bill

Trigger to send an invoice to a target player

## Event

```lua
TriggerServerEvent("billing_ui:sendBill", targetId, societyName, reason, amount)
```

### Parameters

| Name          | Data Type | Description                                                 |
| ------------- | --------- | ----------------------------------------------------------- |
| `targetId`    | integer   | Target player server ID                                     |
| `societyName` | string    | Society name (it will receive the money from the paid bill) |
| `reason`      | string    | The reason of the invoice                                   |
| `amount`      | integer   | The amount of the invoice                                   |

## Example

```lua
local closestPlayer, closestDist = ESX.Game.GetClosestPlayer()
local targetId = GetPlayerServerId(closestPlayer)
local societyName = "society_police"
local reason = "Speed limit"
local amount = 500

TriggerServerEvent("billing_ui:sendBill", targetId, societyName, reason, amount)
```
