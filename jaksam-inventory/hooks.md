# Hooks
Hooks are a way to modify the behavior of the inventory system. They are registered on the server and can be used to modify the behavior of the inventory system, for example to prevent players from moving items to a specific inventory. There are some examples of hooks in `jaksam_inventory/_hooks` folder

## Use Case Examples
- Prevent players from stealing items that have the 'sole_owner' metadata field (e.g., VIP items)
- Prevent players from moving police weapons into their personal inventory
- Allow only one backpack per player inventory
- Crafting items by dragging a specific item over another item (for example dragging bread on meat can make a sandwich)

## API Functions

### Register a Hook
```lua
exports['jaksam_inventory']:registerHook(eventName, callback, options, priority)
```

**Parameters:**
- `eventName` (string): The name of the hook event to listen for (list of available events below)
- `callback` (function): The function to execute when the hook is triggered
- `options` (table, optional): Filters and configuration options (list of available options below)
- `priority` (number, optional): Execution priority (higher numbers execute first, default: 0)

**Returns:**
- `hookId` (string): Unique identifier for the registered hook (used to unregister the hook)

### Unregister a Hook
```lua
exports['jaksam_inventory']:unregisterHook(hookId)
```

**Parameters:**
- `hookId` (string): The unique identifier returned when registering the hook

### Unregister All Resource Hooks
```lua
exports['jaksam_inventory']:unregisterResourceHooks(resourceName)
```

**Parameters:**
- `resourceName` (string): Name of the resource to unregister all hooks for

## Options Parameter

The options parameter accepts a table with filters to optimize performance:

### Common Filters (All Events)
```lua
local options = {
    -- Debug: Print to console when hook triggers
    print = true,
    
    -- Only trigger for specific items
    itemNameFilter = {
        bread = true,
        weapon_pistol = true
    },
    
    -- Only trigger for specific item types
    itemTypeFilter = {
        weapon = true,
        currency = true
    }
}
```

### Inventory Filters (onItemAdded, onItemRemoved)
```lua
local options = {
    -- Filter by inventory type (recommended)
    inventoryTypeFilter = {
        player = true,
        stash = true
    },
    
    -- Filter by specific inventory patterns (advanced)
    inventoryFilter = {
        "player:.*",      -- All players
        "stash_police"    -- Specific stash
    }
}
```

### Transfer Filters (onItemTransferred only)
```lua
local options = {
    -- Filter source inventory by type
    inventoryFromTypeFilter = { player = true },
    
    -- Filter source inventory by name pattern
    inventoryFromFilter = {
        "player:.*",      -- All players
        "vehicle:123"     -- Specific vehicle
    },
    
    -- Filter destination inventory by type
    inventoryToTypeFilter = { stash = true },
    
    -- Filter destination inventory by name pattern
    inventoryToFilter = {
        "stash_police",   -- Specific stash
        "container:.*"    -- All containers
    },
    
    -- Only intra-inventory moves (drag within same inventory)
    intraInventoryOnly = true
}
```

## Available Hook Events

### onItemAdded
Triggered when an item is added to an inventory.

**Payload:**
```lua
payload = {
    inventoryId = "player:1",
    itemName = "bread",
    amount = 5,
    metadata = {durability = 100}, -- Item metadata (can be nil)
    slotId = 1,
}
```

### onItemRemoved
Triggered when an item is removed from an inventory.

**Payload:**
```lua
payload = {
    inventoryId = "player:1",
    itemName = "bread",
    amount = 3,
    metadata = {durability = 80},
    slotId = 1
}
```

### onItemTransferred
Triggered when an item is transferred between inventories (including intra-inventory moves)

**Payload:**
```lua
payload = {
    playerId = 1,
    inventoryIdFrom = "player:1",
    inventoryIdTo = "stash_police",
    slotIdFrom = 1,
    slotIdTo = 5,
    itemName = "weapon_pistol",
    amount = 1,
    metadata = {ammo = 12}
}
```

## Hook Behavior

- **Priority**: Higher numbers execute first (default: 0)
- **Return Values**:
  - `return nil` or `return true`: Allow the action to continue
  - `return false, "message", "notifyType"`: Prevents the action and stops further hook execution
  - The message parameter is optional and will be displayed to the player
  - The notifyType parameter is optional and can be "error", "success", "info"

## Quick Examples

### Block Police Weapons in Player Inventory
```lua
exports['jaksam_inventory']:registerHook("onItemTransferred", function(payload)
    local item = Script.getStaticItem(payload.itemName)
    if item?.policeOnly then
        return false, "Only police can have this weapon"
    end
end, {
    itemTypeFilter = {weapon = true},
    inventoryToTypeFilter = {player = true}
})
```

### One Backpack Per Player
```lua
exports['jaksam_inventory']:registerHook("onItemAdded", function(payload)
    local backpackCount = Script.getTotalItemAmount(payload.inventoryId, "backpack")
    if backpackCount >= 1 then
        return false, "You can only have one backpack"
    end
end, {
    itemNameFilter = {backpack = true},
    inventoryTypeFilter = {player = true}
})
```

### Simple Crafting (Drag Items Together)
```lua
exports['jaksam_inventory']:registerHook("onItemTransferred", function(payload)
    local sourceItem = Script.getItemFromSlot(payload.inventoryIdFrom, payload.slotIdFrom)
    local targetItem = Script.getItemFromSlot(payload.inventoryIdTo, payload.slotIdTo)
    if not targetItem then return end -- Dragged over an empty slot

    if sourceItem.name == "bread" and targetItem.name == "meat" then
        Script.removeItem(payload.inventoryIdFrom, "bread", 1, payload.slotIdFrom)
        Script.removeItem(payload.inventoryIdFrom, "meat", 1, payload.slotIdTo)
        Script.addItem(payload.inventoryIdFrom, "sandwich", 1)
        return false, "You crafted a sandwich", "success"
    end
end, {intraInventoryOnly = true})
```

### Filter by Specific Inventory Name
```lua
-- Only trigger when items are added to police stash
exports['jaksam_inventory']:registerHook("onItemAdded", function(payload)
    print("Item added to police stash:", payload.itemName)
end, {
    inventoryFilter = {"stash_police"}
})
```

## Best Practices

1. **Use Filters**: Always use appropriate filters to avoid unnecessary hook executions
2. **Early Returns**: Use early returns to exit hooks when conditions aren't met
3. **Performance**: Keep hook logic lightweight to avoid impacting inventory performance