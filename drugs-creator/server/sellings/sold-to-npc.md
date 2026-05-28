# Sold to NPC

Triggered after a NPC selling sale

## Event

```lua
RegisterNetEvent("drugs_creator:soldToNPC", function(playerId, drugName, drugQuantity, totalDrugPrice, accountName)

end)
```

### Parameters

| Name             | Data Type | Description                                      |
| ---------------- | --------- | ------------------------------------------------ |
| `playerId`       | int       | Player server ID                                 |
| `drugName`       | string    | Item ID of the drug just sold                    |
| `drugQuantity`   | int       | Item quantity sold                               |
| `totalDrugPrice` | int       | Total money that the player received             |
| `accountName`    | string    | Account type used for reward (money, black_money, etc.) |

## Example

```lua
RegisterNetEvent("drugs_creator:soldToNPC", function(playerId, drugName, drugQuantity, totalDrugPrice, accountName)
    local xPlayer = ESX.GetPlayerFromId(playerId)

    local random = math.random(1, 2)

    if(drugName == "weed" and random == 1) then
        xPlayer.addInventoryItem("weed", 3)

        xPlayer.showNotification("Here you have 3 bonus weed")
    end
    
    print("Player received " .. totalDrugPrice .. " in " .. accountName)
end)
```
