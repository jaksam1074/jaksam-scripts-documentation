# Create bill

## Export

```lua
exports["billing_ui"]:createBill(senderIdentifier, targetIdentifier, reason, amount, target, targetType)
```

### Parameters

| Name               | Data Type | Description                                                                                                                                                                                                                                                                                 |
| ------------------ | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `senderIdentifier` | string    | <p>The identifier of the player who creates the invoice<br><strong>In QBCore it's the citizen ID</strong></p>                                                                                                                                                                               |
| `targetIdentifier` | string    | <p>The identifier of the player who receives the invoice<br><strong>In QBCore it's the citizen ID</strong></p>                                                                                                                                                                              |
| `reason`           | string    | The reason of the invoice                                                                                                                                                                                                                                                                   |
| `amount`           | integer   | The amount of the invoice                                                                                                                                                                                                                                                                   |
| `target`           | string    | <p>Who will receive the payment of the invoice<br>- If <code>targetType</code> it's <code>player</code> the target will be an identifier (or citizen ID in QBCore)<br>- If <code>targetType</code> it's <code>society</code> the target will be for example <code>society_police</code></p> |
| `targetType`       | string    | `player` or `society`                                                                                                                                                                                                                                                                       |

## Example

```lua
-- ESX example
RegisterCommand("sendInvoiceToOfflinePlayer", function(playerId, args)
    local senderIdentifier = ESX.GetPlayerFromId(playerId).identifier
    local targetIdentifier = args[1] -- Example 6833b871ee066492978077ef154480366a2374b
    local reason = args[2] -- Example "Speed limit exceeded"
    local amount = tonumber(args[3]) -- Example 5000
    local target = "society_police"
    local targetType = "society"
    
    exports["billing_ui"]:createBill(senderIdentifier, targetIdentifier, reason, amount, target, targetType)
end)

-- QBCore example
RegisterCommand("sendInvoiceToOfflinePlayer", function(playerId, args)
    local senderIdentifier = QBCore.Functions.GetPlayer(playerId).PlayerData.citizenid
    local targetIdentifier = args[1] -- Example GPI46753
    local reason = args[2] -- Example "Speed limit exceeded"
    local amount = tonumber(args[3]) -- Example 5000
    local target = "society_police"
    local targetType = "society"
    
    exports["billing_ui"]:createBill(senderIdentifier, targetIdentifier, reason, amount, target, targetType)
end)
```
