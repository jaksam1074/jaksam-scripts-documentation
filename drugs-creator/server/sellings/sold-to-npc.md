# Sold to NPC

Triggered after a NPC selling sale

## Event

```lua
RegisterNetEvent("drugs_creator:soldToNPC", function(playerId, drugName, drugQuantity, totalDrugPrice)

end)
```

### Parameters

| Name             | Data Type | Description                          |
| ---------------- | --------- | ------------------------------------ |
| `playerId`       | int       | Player server ID                     |
| `drugName`       | string    | Item ID of the drug just sold        |
| `drugQuantity`   | int       | Item quantity sold                   |
| `totalDrugPrice` | int       | Total money that the player received |

## Example

```lua
RegisterNetEvent("drugs_creator:soldToNPC", function(playerId, drugName, drugQuantity, totalDrugPrice)
    local xPlayer = ESX.GetPlayerFromId(playerId)

    local random = math.random(1, 2)

    if(drugName == "weed" and random == 1) then
        xPlayer.addInventoryItem("weed", 3)

        xPlayer.showNotification("Here you have 3 bonus weed")
    end
end)
```
