# Server Events

The inventory system triggers various events when items are added, removed, or transferred. You can listen to these events to implement custom logic

## onInventoryItemAdded

Triggered when an item is successfully added to an inventory

### Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| inventoryId | string | The inventory identifier. For players, this is the character identifier |
| itemName | string | The name of the item added |
| amount | number | The quantity added |
| metadata | table | The item's metadata |
| slotId | number/nil | The slot where the item was added (can be nil a slot wasn't specified when adding item) |

### Example

```lua
AddEventHandler('jaksam_inventory:onInventoryItemAdded', function(inventoryId, itemName, amount, metadata, slotId)
    local inventoryType = exports['jaksam_inventory']:getInventoryType(inventoryId)
    if inventoryType ~= 'player' then return end -- Only handle player inventories

    print(string.format("Item %s (x%d) added to inventory %s", itemName, amount, inventoryId))
    
    -- For QBCore: Get player by character identifier
    local Player = exports['qb-core']:GetPlayerByCitizenId(inventoryId)
    if Player then
        local playerId = Player.PlayerData.source
        print(string.format("Player %d added item %s", playerId, itemName))
    end
    
    -- For ESX: Get player by character identifier
    -- local xPlayer = ESX.GetPlayerFromIdentifier(inventoryId)
    -- if xPlayer then
    --     local playerId = xPlayer.source
    --     print(string.format("Player %d added item %s", playerId, itemName))
    -- end
end)
```

---

## onInventoryItemRemoved

Triggered when an item is successfully removed from an inventory

### Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| inventoryId | string | The inventory identifier. For players, this is the character identifier |
| itemName | string | The name of the item removed |
| amount | number | The quantity removed |
| metadata | table | The item's metadata |
| slotId | number/nil | The slot from which the item was removed (can be nil a slot wasn't specified when removing item) |

### Example

```lua
AddEventHandler('jaksam_inventory:onInventoryItemRemoved', function(inventoryId, itemName, amount, metadata, slotId)
    local inventoryType = exports['jaksam_inventory']:getInventoryType(inventoryId)
    if inventoryType ~= 'player' then return end -- Only handle player inventories

    print(string.format("Item %s (x%d) removed from inventory %s", itemName, amount, inventoryId))
    
    -- For QBCore: Get player by character identifier
    local Player = exports['qb-core']:GetPlayerByCitizenId(inventoryId)
    if Player then
        local playerId = Player.PlayerData.source
        print(string.format("Player %d removed item %s", playerId, itemName))
        
        -- Example: Log to Discord or database
        -- exports['your_logs']:log({
        --     event = "item_removed",
        --     playerId = playerId,
        --     item = itemName,
        --     amount = amount
        -- })
    end
    
    -- For ESX: Get player by character identifier
    -- local xPlayer = ESX.GetPlayerFromIdentifier(inventoryId)
    -- if xPlayer then
    --     local playerId = xPlayer.source
    --     print(string.format("Player %d removed item %s", playerId, itemName))
    -- end
end)
```

---

## onInventoryItemTransferred

Triggered when an item is successfully transferred from one inventory to another.

### Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| inventoryIdFrom | string | The source inventory identifier. For players, this is the character identifier |
| inventoryIdTo | string | The destination inventory identifier. For players, this is the character identifier |
| itemName | string | The name of the item transferred |
| amount | number | The quantity transferred |
| metadata | table | The item's metadata |
| slotIdFrom | number/nil | The slot from which the item was transferred |
| slotIdTo | number/nil | The slot to which the item was transferred |

### Example

```lua
AddEventHandler('jaksam_inventory:onInventoryItemTransferred', function(inventoryIdFrom, inventoryIdTo, itemName, amount, metadata, slotIdFrom, slotIdTo)
    local inventoryTypeFrom = exports['jaksam_inventory']:getInventoryType(inventoryIdFrom)
    local inventoryTypeTo = exports['jaksam_inventory']:getInventoryType(inventoryIdTo)
    if inventoryTypeFrom ~= 'player' or inventoryTypeTo ~= 'player' then return end -- Only handle player inventories

    print(string.format("Item %s (x%d) transferred from %s to %s", itemName, amount, inventoryIdFrom, inventoryIdTo))
    
    -- For QBCore
        local Player = exports['qb-core']:GetPlayerByCitizenId(inventoryId)
        if Player then
            local playerId = Player.PlayerData.source
            print(string.format("Player %d transferred item %s (x%d) to player %d", playerId, itemName, amount, playerIdTo))
        end
    end
    
    print(string.format("Item %s (x%d) transferred from %s to %s", itemName, amount, inventoryIdFrom, inventoryIdTo))
end)
```