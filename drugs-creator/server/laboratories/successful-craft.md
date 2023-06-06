# Successful craft

Triggered after a successful craft in a laboratory

## Event

```lua
RegisterNetEvent("drugs_creator:laboratory:successfulCraft", function(playerId, ingredientsUsed, itemsToGive, laboratoryId)

end)
```

### Parameters

| Name              | Data Type   | Description                                                                                                    |
| ----------------- | ----------- | -------------------------------------------------------------------------------------------------------------- |
| `playerId`        | int         | Player server ID                                                                                               |
| `ingredientsUsed` | table       | Table containing the ingredients used. Key = ingredient name, Value = intedient quantity                       |
| `itemsToGive`     | table/array | An array containing a table of the items to give. The table will have `itemName` and `itemQuantity` properties |
| `laboratoryId`    | int         | laboratory ID                                                                                                  |

## Example

```lua
-- An example for a xp system
RegisterNetEvent("drugs_creator:laboratory:successfulCraft", function(playerId, ingredientsUsed, itemsToGive, laboratoryId)
    for k, resultItem in pairs(itemsToGive) do
        local itemName = resultItem.itemName
        local quantity = resultItem.itemQuantity

        TriggerEvent("xp_system:addXp", playerId, itemQuantity)
    end
end)
```
