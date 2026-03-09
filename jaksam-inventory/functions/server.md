# Compatibility
This script works with other popular inventory systems, like es_extended, qb-inventory, and ox_inventory

For ESX and QBCore functions, the setup is done automatically. But, if you want to keep using exports from ox_inventory or qb-inventory for compatibility, you need to turn on this option in the file: `jaksam_inventory/integrations/sv_integrations.lua`

# Server functions
Here there are built-in exports of jaksam's inventory

## addItem
Adds items to an inventory with support for metadata and specific slot placement

```lua
exports['jaksam_inventory']:addItem(inventoryId, itemName, amount, metadata, slotId)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to add items to
  - Can be a player server ID or inventory ID
- `itemName`: string
  - The name of the item to add
- `amount`: number
  - How many items to add
- `metadata`: table (optional)
  - Additional data for the item (e.g. weapon serial, item durability)
- `slotId`: number (optional)
  - Specific slot to place the item in

### Returns

- `success`: boolean
  - true if items were added successfully
- `resultCode`: string
  - Error message if the operation failed

### Example

```lua
-- Add 5 bread to a player's inventory
local success, result = exports['jaksam_inventory']:addItem(1, 'bread', 5)

-- Add a weapon with metadata
local success, result = exports['jaksam_inventory']:addItem(1, 'WEAPON_PISTOL', 1, {
    serial = "ABC123",
    ammo = 12
})

-- Add item to specific slot
local success, result = exports['jaksam_inventory']:addItem(1, 'bread', 1, nil, 5) -- slot 5
```

## addItemToTrunk
Adds items to a vehicle trunk using only the vehicle plate, automatically resolving the full inventory ID

```lua
exports['jaksam_inventory']:addItemToTrunk(plate, itemName, amount, metadata, slotId)
```

### Parameters

- `plate`: string
  - The vehicle license plate
- `itemName`: string
  - The name of the item to add
- `amount`: number
  - How many items to add
- `metadata`: table (optional)
  - Additional data for the item
- `slotId`: number (optional)
  - Specific slot to place the item in

### Returns

- `success`: boolean
  - true if items were added successfully
- `resultCode`: string
  - Error message if the operation failed (e.g., "vehicle_not_found")
- `notificationType`: string
  - Type of notification to show to the user

### Example

```lua
-- Add 5 water bottles to vehicle trunk
local plate = GetVehicleNumberPlateText(vehicle)
local success, result = exports['jaksam_inventory']:addItemToTrunk(plate, 'water', 5)

if not success then
    print("Failed to add item: " .. result)
end

-- Add item with metadata
local success = exports['jaksam_inventory']:addItemToTrunk("ABC 123", 'phone', 1, {
    number = "555-0123"
})
```

### Notes

- Works with owned vehicles (even if not spawned/in garage)
- Works with NPC vehicles (if currently spawned)
- Automatically creates trunk inventory if it doesn't exist
- For owned vehicles, inventory is persistent (saved to database)

## addItemToGlovebox
Adds items to a vehicle glovebox using only the vehicle plate, automatically resolving the full inventory ID

```lua
exports['jaksam_inventory']:addItemToGlovebox(plate, itemName, amount, metadata, slotId)
```

### Parameters

- `plate`: string
  - The vehicle license plate
- `itemName`: string
  - The name of the item to add
- `amount`: number
  - How many items to add
- `metadata`: table (optional)
  - Additional data for the item
- `slotId`: number (optional)
  - Specific slot to place the item in

### Returns

- `success`: boolean
  - true if items were added successfully
- `resultCode`: string
  - Error message if the operation failed (e.g., "vehicle_not_found")
- `notificationType`: string
  - Type of notification to show to the user

### Example

```lua
-- Add documents to glovebox
local plate = GetVehicleNumberPlateText(vehicle)
local success = exports['jaksam_inventory']:addItemToGlovebox(plate, 'documents', 1)

-- Add multiple items
local success = exports['jaksam_inventory']:addItemToGlovebox("XYZ 789", 'money', 500)
```

### Notes

- Works with owned vehicles (even if not spawned/in garage)
- Works with NPC vehicles (if currently spawned)
- Automatically creates glovebox inventory if it doesn't exist
- For owned vehicles, inventory is persistent (saved to database)

## removeItemFromTrunk
Removes items from a vehicle trunk using only the vehicle plate, automatically resolving the full inventory ID

```lua
exports['jaksam_inventory']:removeItemFromTrunk(plate, itemName, amount, metadata, slotId)
```

### Parameters

- `plate`: string
  - The vehicle license plate
- `itemName`: string
  - The name of the item to remove
- `amount`: number
  - How many items to remove
- `metadata`: table (optional)
  - Metadata to match for removal (optional filtering)
- `slotId`: number (optional)
  - Specific slot to remove from

### Returns

- `success`: boolean
  - true if items were removed successfully
- `resultCode`: string
  - Error message if the operation failed
- `notificationType`: string
  - Type of notification to show to the user

### Example

```lua
-- Remove 3 water bottles from trunk
local plate = GetVehicleNumberPlateText(vehicle)
local success = exports['jaksam_inventory']:removeItemFromTrunk(plate, 'water', 3)

-- Remove from specific slot
local success = exports['jaksam_inventory']:removeItemFromTrunk("ABC 123", 'weapon', 1, nil, 5)
```

### Notes

- Vehicle must exist (owned vehicle in database or NPC vehicle currently spawned)
- Returns false with "vehicle_not_found" if vehicle doesn't exist

## removeItemFromGlovebox
Removes items from a vehicle glovebox using only the vehicle plate, automatically resolving the full inventory ID

```lua
exports['jaksam_inventory']:removeItemFromGlovebox(plate, itemName, amount, metadata, slotId)
```

### Parameters

- `plate`: string
  - The vehicle license plate
- `itemName`: string
  - The name of the item to remove
- `amount`: number
  - How many items to remove
- `metadata`: table (optional)
  - Metadata to match for removal (optional filtering)
- `slotId`: number (optional)
  - Specific slot to remove from

### Returns

- `success`: boolean
  - true if items were removed successfully
- `resultCode`: string
  - Error message if the operation failed
- `notificationType`: string
  - Type of notification to show to the user

### Example

```lua
-- Remove documents from glovebox
local plate = GetVehicleNumberPlateText(vehicle)
local success = exports['jaksam_inventory']:removeItemFromGlovebox(plate, 'documents', 1)

if not success then
    print("Document not found in glovebox")
end
```

### Notes

- Vehicle must exist (owned vehicle in database or NPC vehicle currently spawned)
- Returns false with "vehicle_not_found" if vehicle doesn't exist

## getInventoryIdFromPlate
Resolves the full inventory ID for a vehicle compartment using only the vehicle plate

```lua
exports['jaksam_inventory']:getInventoryIdFromPlate(plate, compartment)
```

### Parameters

- `plate`: string
  - The vehicle license plate
- `compartment`: string
  - Either "trunk" or "glovebox"

### Returns

- `inventoryId`: string | nil
  - The full inventory ID (format: "vehicle:plate:model:compartment")
  - nil if vehicle not found

### Example

```lua
-- Get trunk inventory ID
local plate = GetVehicleNumberPlateText(vehicle)
local trunkId = exports['jaksam_inventory']:getInventoryIdFromPlate(plate, "trunk")

if trunkId then
    print("Trunk ID: " .. trunkId)
    -- Now you can use standard inventory functions
    local inventory = exports['jaksam_inventory']:getInventory(trunkId)
end

-- Get glovebox inventory ID
local gloveboxId = exports['jaksam_inventory']:getInventoryIdFromPlate("ABC 123", "glovebox")
```

### Notes

- Searches in this order:
  1. Owned vehicles database (ESX: `owned_vehicles`, QBCore: `player_vehicles`)
  2. Existing inventories in `jaksam_inventory` table
  3. Currently spawned vehicles (GetAllVehicles - NPC vehicles)
- For owned vehicles, automatically creates inventory if it doesn't exist
- Created inventories are persistent for owned vehicles, temporary for NPC vehicles
- Works even if vehicle is not currently spawned (garage)

## canCarryItem
Checks if an inventory has space for additional items, considering both weight and slot limits

```lua
exports['jaksam_inventory']:canCarryItem(inventoryId, itemName, amount)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to check
  - Can be a player server ID or inventory ID
- `itemName`: string
  - The name of the item to check
- `amount`: number
  - How many items to check for

### Returns

- `boolean`
  - true if the inventory can carry the items
  - false if adding would exceed weight or slot limits

### Example

```lua
-- Check if player can carry 5 bread
local canCarry = exports['jaksam_inventory']:canCarryItem(1, 'bread', 5)

if canCarry then
    -- Safe to add items
    exports['jaksam_inventory']:addItem(1, 'bread', 5)
end
```

## canSwapItem
Checks if swapping firstItem (removing firstItemCount) with testItem (adding testItemCount) is possible

```lua
exports['jaksam_inventory']:canSwapItem(inventoryId, firstItem, firstItemCount, testItem, testItemCount)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to check
  - Can be a player server ID or inventory ID
- `firstItem`: string
  - The name of the item to check
- `firstItemCount`: number
  - How many items to remove
- `testItem`: string
  - The name of the item to add
- `testItemCount`: number
  - How many items to add

### Returns

- `boolean`
  - true if the inventory can swap the items
  - false if swapping is not possible

### Example

```lua
-- Check if player can swap 5 bread for 1 water
local playerId = 1
local canSwap = exports['jaksam_inventory']:canSwapItem(playerId, 'bread', 5, 'water', 1)

if canSwap then
    exports['jaksam_inventory']:removeItem(playerId, 'bread', 5)
    exports['jaksam_inventory']:addItem(playerId, 'water', 1)
end
```

## clearInventory
Removes all items from an inventory, with optional exclusion of specific items

```lua
exports['jaksam_inventory']:clearInventory(inventoryId, excludedItems)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to clear
  - Can be a player server ID or inventory ID
- `excludedItems`: string | table (optional)
  - Items to exclude from clearing (keep in inventory)
  - Can be a single item name (string) or an array of item names (table)
  - If not provided, all items will be removed

### Returns

- `success`: boolean
  - true if inventory was cleared successfully
  - false if inventory doesn't exist or database update failed

### Example

```lua
local playerId = 14

-- Clear all items from player inventory
local success = exports['jaksam_inventory']:clearInventory(playerId)

-- Clear inventory but keep specific items
local success = exports['jaksam_inventory']:clearInventory(playerId, 'phone') -- keep phone

-- Clear inventory but keep multiple items
local success = exports['jaksam_inventory']:clearInventory(1, {'phone', 'id_card', 'driver_license'})

-- Clear stash inventory
local success = exports['jaksam_inventory']:clearInventory('police_stash_1')
```

## createInventory
Creates a new inventory in both database and memory (depending on options). If an inventory with the same ID already exists, returns the existing one without modifying it

```lua
exports['jaksam_inventory']:createInventory(id, label, options, items, inventoryType, metadata)
```

### Parameters

- `id`: string | nil
  - Unique identifier for the inventory. If nil, a random ID is generated
- `label`: string | nil
  - Display name for the inventory. If nil, a translation based on inventory type will be used
- `options`: table (optional)
  - Configuration options for the inventory:
  - `maxWeight` (number, optional): Maximum weight capacity
  - `maxSlots` (number, optional): Maximum number of slots
  - `columns` (number, optional): Number of columns for grid display in the UI (for example you can make an inventory that's total slots is 10, but only has 2 columns, so it will be a 2x5 grid)
  - `temporary` (boolean, optional): If true, the inventory is not saved to the database and will be lost on script restart
  - `prefillItems` (table, optional): Random loot configuration. Items are picked via weighted selection without replacement. Structure:
    - `minTypes` (number, optional): Minimum number of different item types to add. Default: 1
    - `maxTypes` (number, optional): Maximum number of different item types to add. Default: pool size
    - `items` (table, **required**): Array of possible items, each entry: `{name = string, chance = number, min = number, max = number, metadata = table?}`
      - `name` (string, **required**): Item name
      - `chance` (number, optional): Relative weight for selection (higher = more likely). Default: 1
      - `min` (number, optional): Minimum amount when picked. Default: 1
      - `max` (number, optional): Maximum amount when picked. Default: 1
      - `metadata` (table, optional): Metadata to attach to the item
  - `revealItems` (table, optional): Progressive item reveal animation when the inventory is opened. Items appear one by one. Structure:
    - `delayPerItem` (number, optional): Milliseconds between each item reveal. Default: 1000
    - `randomOrder` (boolean, optional): If true, items are revealed in random order instead of slot order. Default: false
  - `slots` (table, optional): Per-slot configuration. Key is the slot number, value is a `SlotConfig` table:
    - `label` (string, optional): Display label for the slot placeholder
    - `image` (string, optional): Placeholder image name shown when slot is empty
    - `opacity` (number, optional): Placeholder image opacity (0.0 - 1.0)
    - `whitelist` (table, optional): Slot-level whitelist. Format: `{itemName = true, ...}`. Takes priority over inventory-level whitelist
    - `blacklist` (table, optional): Slot-level blacklist. Format: `{itemName = true, ...}`. Applied before inventory whitelist
  - `whitelist` (table, optional): Inventory-level item whitelist (used as fallback if a slot has no filter). Format: `{itemName = true, ...}`
  - `blacklist` (table, optional): Inventory-level item blacklist. Format: `{itemName = true, ...}`
  - `allowedJobs` (table, optional): Jobs allowed to access this inventory. Format: `{police = true, sheriff = true}`
  - `allowedIdentifiers` (table, optional): Character identifiers allowed to access this inventory. Format: `{charIdentifier = true, ...}`
  - `disableIncoming` (boolean, optional): If true, items cannot be transferred into this inventory by the player
  - `disableOutgoing` (boolean, optional): If true, items cannot be transferred out of this inventory by the player
  - `dropDisabled` (boolean, optional): If true, items cannot be dropped from this inventory
  - `noLimitDrag` (boolean, optional): If true, dragging ignores the amount selection dialog and moves the full stack. Used internally for shops
- `items`: table (optional)
  - Static items to add when the inventory is first created. Array format: `{{itemName, amount, metadata}, ...}`
  - Ignored if the inventory already exists in the database
- `inventoryType`: string (optional)
  - Type of inventory. Default: "stash". Other values: "player", "trunk", "glovebox"
- `metadata`: table (optional)
  - Additional metadata for the inventory

### Returns

- `inventory`: Inventory | nil
  - The created (or existing) inventory table, or nil if creation failed
  - Structure: `{id, label, options, items, type, totalWeight, metadata}`

### Example

```lua
-- Example: Create a loot crate with dynamic loot based on rarity
-- Don't forget to secure the event somehow depending on your use case, otherwise cheaters can simply trigger the event to get free loot
RegisterNetEvent('myresource:openLootCrate', function(rarity)
    local playerId = source
    
    -- Define loot pools based on rarity
    local lootPools = {
        common = {
            minTypes = 1,
            maxTypes = 2,
            items = {
                { name = "water",   chance = 15, min = 1, max = 3 },
                { name = "bread",   chance = 15, min = 1, max = 2 },
                { name = "bandage", chance = 10, min = 1, max = 2 },
            }
        },
        rare = {
            minTypes = 2,
            maxTypes = 4,
            items = {
                { name = "water",         chance = 10, min = 2, max = 4 },
                { name = "bread",         chance = 8,  min = 2, max = 3 },
                { name = "bandage",       chance = 8,  min = 2, max = 3 },
                { name = "lockpick",      chance = 5,  min = 1, max = 2 },
                { name = "weapon_pistol", chance = 2,  min = 1, max = 1 },
            }
        },
        legendary = {
            minTypes = 3,
            maxTypes = 5,
            items = {
                { name = "water",         chance = 8,  min = 3, max = 5 },
                { name = "bandage",       chance = 8,  min = 3, max = 4 },
                { name = "lockpick",      chance = 6,  min = 2, max = 3 },
                { name = "weapon_pistol", chance = 4,  min = 1, max = 1 },
                { name = "weapon_rifle",  chance = 2,  min = 1, max = 1 },
            }
        }
    }
    
    local selectedLoot = lootPools[rarity] or lootPools.common
    
    local inventory = exports['jaksam_inventory']:createInventory(
        nil, -- Auto generate ID
        "Loot Crate (" .. rarity .. ")", -- Dynamic label
        {
            temporary = true, -- Inventory will be lost on script restart
            maxSlots = 5,
            maxWeight = 50.0,
            disableIncoming = true, -- Items cannot be added to this inventory by the player
            prefillItems = selectedLoot,
            revealItems = {
                delayPerItem = 1000,
                randomOrder = true
            }
        },
        nil,
        'stash',
        nil
    )
    
    -- Open the inventory interface for the player
    if inventory then
        exports['jaksam_inventory']:forceOpenInventory(playerId, inventory.id)
    end
end)
```

```lua
-- Create a persistent stash with fixed starting items
local inventory = exports['jaksam_inventory']:createInventory(
    "welcome_kit_" .. charId,
    "Welcome Kit",
    { maxSlots = 5, maxWeight = 20.0 },
    {
        {"bread", 3, nil},
        {"water", 2, nil},
    },
    'stash',
    nil
)
```

### Notes

- If `id` already exists, the existing inventory is returned as is, static `items` and `prefillItems` are NOT re-applied
- `prefillItems` uses weighted random selection **without replacement** (each item type can only be picked once)
- `prefillItems` is processed via `options`, while static `items` is a separate parameter. they serve different purposes
- Use `temporary = true` for ephemeral inventories (lootboxes, event rewards) to avoid database bloat

## forceOpenInventory
Forces an inventory to be opened for a specific player without permission checks

```lua
exports['jaksam_inventory']:forceOpenInventory(playerId, inventoryId)
```

### Parameters

- `playerId`: number
  - The server ID of the player who will see the inventory
- `inventoryId`: string | number
  - The inventory ID to open
  - Can be a player server ID (number) or inventory ID (string)

### Returns

This function doesn't return any value

### Example

```lua
-- Open a stash for a player
local playerId = 1
exports['jaksam_inventory']:forceOpenInventory(playerId, 'police_stash_1')

-- Open another player's inventory (search/rob)
local targetPlayerId = 2
exports['jaksam_inventory']:forceOpenInventory(playerId, targetPlayerId)

-- Open inventory from a custom menu/UI
RegisterNetEvent('myresource:openCustomStorage', function(storageId)
    local playerId = source
    exports['jaksam_inventory']:forceOpenInventory(playerId, storageId)
end)
```

## getInventory
Gets complete data about an inventory including its items, weight limits, and metadata

```lua
exports['jaksam_inventory']:getInventory(inventoryId)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to get data for
  - Can be a player server ID (number) or inventory ID (string)

### Returns

- `inventory`: table | nil
  - Table containing the inventory data with the following structure:
  ```lua
  {
      id = string,          -- Unique identifier of the inventory
      label = string,       -- Display name of the inventory
      type = string,        -- Type of inventory (e.g. "player", "stash", "trunk")
      options = table,      -- Inventory options and settings
      items = table,        -- Items contained in the inventory
      totalWeight = number, -- Current total weight of inventory
      limits = {
          maxSlots = number,  -- Maximum number of slots
          maxWeight = number  -- Maximum weight capacity
      },
      metadata = table      -- Additional inventory metadata
  }
  ```

### Example

```lua
-- Get a player's inventory
local inventory = exports['jaksam_inventory']:getInventory(1) -- player with server ID 1

-- Get a stash inventory
local stashInv = exports['jaksam_inventory']:getInventory('police_stash_1')

if inventory then
    print(inventory.totalWeight) -- prints current weight
    print(inventory.limits.maxWeight) -- prints max weight allowed
    print(json.encode(inventory.items, {indent = true})) -- {["SLOT-4"] = {name = "itemName", amount = 1, metadata = {}}}
end
```

## getItemFromSlot
Gets an item from a specific slot in an inventory

```lua
exports['jaksam_inventory']:getItemFromSlot(inventoryId, slotId, returnRaw)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to get the item from
  - Can be a player server ID (number) or inventory ID (string)
- `slotId`: number
  - The slot number to get the item from

### Returns

- `item`: table | nil
  - The item in the slot, or nil if the slot is empty
  - Item structure:
  ```lua
  {
      name = string,     -- Item name
      amount = number,   -- Item amount
      metadata = table   -- Item metadata
  }
  ```

### Example

```lua
-- Get item from player's slot 5
local playerId = 1
local item = exports['jaksam_inventory']:getItemFromSlot(playerId, 5)

if item then
    print('Item name:', item.name)
    print('Amount:', item.amount)
    print('Metadata:', json.encode(item.metadata))

    item.metadata.durability = 50 -- update metadata
    exports['jaksam_inventory']:setItemMetadataInSlot(playerId, 5, item.metadata) -- save metadata
end

-- Get item from stash
local stashItem = exports['jaksam_inventory']:getItemFromSlot('police_stash_1', 3)
```

## getItemByName
Gets the first item found in an inventory by its name, with optional metadata filtering

```lua
exports['jaksam_inventory']:getItemByName(inventoryId, itemName, metadata)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to search in
  - Can be a player server ID (number) or inventory ID (string)
- `itemName`: string
  - The name of the item to search for
- `metadata`: table (optional)
  - Metadata to match against when searching
  - If provided, only items with matching metadata will be returned

### Returns

- `item`: table | nil
  - The first item found matching the criteria, or nil if not found
  - Item structure:
  ```lua
  {
      name = string,     -- Item name
      amount = number,   -- Item amount in that specific slot
      metadata = table   -- Item metadata or nil
  }
  ```
- `slotId`: number | nil
  - The raw slot ID where the item was found (1-based index)
  - nil if item not found

### Example

```lua
-- Get first bread item in player's inventory
local playerId = 1
local item, slotId = exports['jaksam_inventory']:getItemByName(playerId, 'bread')

if item then
    print('Found bread in slot:', slotId)
    print('Amount in this slot:', item.amount)
    print('Item metadata:', json.encode(item.metadata))
end

-- Get weapon with specific serial number
local weapon, weaponSlot = exports['jaksam_inventory']:getItemByName(playerId, 'WEAPON_PISTOL', {
    serial = "ABC123"
})

if weapon then
    print('Found weapon in slot:', weaponSlot)
    print('Weapon ammo:', weapon.metadata.ammo)
end
```

## getItemsByName
Gets all items from an inventory by name, with optional metadata filtering

```lua
exports['jaksam_inventory']:getItemsByName(inventoryId, itemName, metadata, strict)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to search in
  - Can be a player server ID (number) or inventory ID (string)
- `itemName`: string
  - The name of the items to search for
- `metadata`: table (optional)
  - Metadata to match against when searching
  - If provided, only items with matching metadata will be returned
- `strict`: boolean (optional)
  - Whether to match the metadata strictly (default: nil)
  - If true, all metadata fields must match exactly

### Returns

- `items`: table
  - Array of all items found matching the criteria
  - Empty table `{}` if no items found
  - Each item in the array has the following structure:
  ```lua
  {
      name = string,     -- Item name
      amount = number,   -- Item amount in that specific slot
      metadata = table,  -- Item metadata or nil
      slot = number      -- Raw slot ID where the item was found (1-based index)
  }
  ```

### Example

```lua
-- Get all bread items in player's inventory
local playerId = 1
local breads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')

print('Found ' .. #breads .. ' bread stacks')
for i = 1, #breads do
    local bread = breads[i]
    print('Slot ' .. bread.slot .. ': ' .. bread.amount .. ' breads')
end

-- Get all weapons with specific metadata (ammo = 0)
local weapons = exports['jaksam_inventory']:getItemsByName(playerId, 'WEAPON_PISTOL', {
    ammo = 0
})

-- Calculate total amount across all slots (export['jaksam_inventory']:getItemTotalAmount is suggested to use instead)
local totalBread = 0
local allBreads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')
for i = 1, #allBreads do
    totalBread = totalBread + allBreads[i].amount
end
print('Total bread amount:', totalBread)

-- Remove all bread from inventory
local breads = exports['jaksam_inventory']:getItemsByName(playerId, 'bread')
for i = 1, #breads do
    exports['jaksam_inventory']:removeItem(playerId, 'bread', breads[i].amount, nil, breads[i].slot)
end
```

### Notes
- Each item includes the `slot` field indicating where it was found
- Use this when you need to process multiple stacks of the same item
- For single item lookups, prefer `getItemByName` for better performance

## getItemLabel
Gets the display label of an item

```lua
exports['jaksam_inventory']:getItemLabel(itemName)
```

### Parameters

- `itemName`: string
  - The name of the item to get the label for

### Returns

- `label`: string | nil
  - The display label of the item
  - nil if item doesn't exist

### Example

```lua
-- Get item label
local label = exports['jaksam_inventory']:getItemLabel('bread')
print(label) -- prints "Bread" or whatever label is set

-- Check if item exists using label (despite this would work the best way would be to use exports['jaksam_inventory']:getStaticItem)
if not exports['jaksam_inventory']:getItemLabel('invalid_item') then
    print('Item does not exist')
end
```

## getTotalItemAmount
Returns the total amount of a specific item in an inventory, including items in containers

```lua
exports['jaksam_inventory']:getTotalItemAmount(inventoryId, itemName, metadata, skipContainers)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to check
- `itemName`: string
  - The name of the item to count
- `metadata`: table (optional)
  - Metadata to match against when counting (if provided, only items with the same metadata AND name will be counted)
- `skipContainers`: boolean (optional)
  - If true, items in containers will not be counted

### Returns

- `totalAmount`: number
  - Total amount of the item in the inventory, including containers (only if skipContainers is false)
- `totalAmountContainersExcluded`: number | nil
  - Total amount excluding containers (only if skipContainers is false)

### Example

```lua
-- Get total amount of bread in inventory
local total = exports['jaksam_inventory']:getTotalItemAmount(1, 'bread')

-- Get amount with specific metadata
local total = exports['jaksam_inventory']:getTotalItemAmount(1, 'weapon_pistol', {
    serial = "ABC123"
})

-- Get amount excluding containers
local total, totalNoContainers = exports['jaksam_inventory']:getTotalItemAmount(1, 'bread', nil, true)
```

## hasItem
Checks if an inventory has a specific item

```lua
exports['jaksam_inventory']:hasItem(inventoryId, itemName, quantity)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to check
- `itemName`: string
  - The name of the item to check
- `quantity`: number (optional)
  - How many items to check for
  - Default is 1

### Returns

- `boolean`
  - true if the inventory has the item
  - false if the inventory does not have the item

### Example

```lua
-- Check if player has 5 bread
local hasItem = exports['jaksam_inventory']:hasItem(1, 'bread', 5)

if hasItem then
    -- Safe to remove items
    exports['jaksam_inventory']:removeItem(1, 'bread', 5)
end
```

## registerUsableItem
Registers a callback function that will be called when an item is used
Framework specific registering item will work anyway, as ESX.RegisterUsableItem and QBCore one

```lua
exports['jaksam_inventory']:registerUsableItem(itemName, callback)
```

### Parameters

- `itemName`: string
  - The name of the item to register
- `callback`: function
  - Function to call when item is used
  - Parameters of callback on ESX: `playerId, itemName, inventoryItem` (`name`, `metadata`, `amount`)
  - Parameters of callback on QBCore: `playerId, inventoryItem` (`name`, `metadata`, `amount`, etc.)

### Returns

- `success`: boolean
  - true if registration was successful

### Example

```lua
-- Register usable item on ESX
exports['jaksam_inventory']:registerUsableItem('bread', function(playerId, itemName, inventoryItem)
    -- Heal player when bread is used
    local plyPed = GetPlayerPed(playerId)
    local health = GetEntityHealth(plyPed)
    SetEntityHealth(plyPed, math.min(health + 20, 200))
end)

-- Register usable item on ESX showing used item metadata
exports['jaksam_inventory']:registerUsableItem('armour', function(playerId, itemName, inventoryItem)
    print("Armor has still " .. inventoryItem.metadata.value .. "% of durability")
end)
```

```lua
-- Register usable item on QBCore
exports['jaksam_inventory']:registerUsableItem('armour', function(playerId, item)
    print("Armor has still " .. item.metadata.value .. "% of durability")
end)
```

## registerStash
Dynamically registers a new stash and creates its server inventory during runtime

```lua
exports['jaksam_inventory']:registerStash(options)
```

### Parameters

- `options`: table
  - Configuration table for the stash with the following fields:
  - `id` (string, optional): Unique ID for the stash. If not provided, one will be autogenerated
  - `label` (string, **required**): Display name for the stash
  - `coords` (vector3 | table, optional): Location where the stash can be accessed via interaction point
  - `maxWeight` (number, optional): Maximum weight capacity. Default: 100
  - `maxSlots` (number, optional): Maximum number of slots. Default: 100
  - `radius` (number, optional): Distance from which players can access the stash. Default: 3.0
  - `isPrivate` (boolean, optional): If true, creates a separate inventory for each player. Default: false
  - `allowedJobs` (table, optional): Table of job names that can access the stash. If nil, stash is public. Example: `{police = true, sheriff = true}`
  - `temporary` (boolean, optional): If true, stash won't be saved to database and lost on script restart. Default: false
  - `startingItems` (table, optional): Items to add when the stash is first created. Format: `{{itemName, amount, metadata}, {itemName2, amount2, metadata2}, ...}`
  - `runtimeOnly` (boolean, optional): If true (default), stash can only be opened programmatically. If false and coords are provided, creates client-side interaction points (jaksam_inventory will handle also stash opening point itself) Default: true

### Returns

- `stashId`: string | nil
  - The ID of the created stash
  - nil if creation failed

### Example

```lua
-- Create a public stash with interaction point (runtimeOnly = false)
local stashId = exports['jaksam_inventory']:registerStash({
    label = "Public Storage",
    coords = vector3(100.0, 200.0, 30.0),
    maxWeight = 500,
    maxSlots = 50,
    radius = 5.0,
    runtimeOnly = false -- Enable interaction points
})

-- Create a job-restricted stash with interaction point
local policeStashId = exports['jaksam_inventory']:registerStash({
    id = "police_evidence",
    label = "Police Evidence Locker",
    coords = vector3(450.0, -990.0, 30.0),
    maxWeight = 1000,
    maxSlots = 100,
    radius = 3.0,
    allowedJobs = {police = true, sheriff = true},
    runtimeOnly = false -- Enable interaction points
})

-- Create a programmatic-only stash (default behavior, runtimeOnly = true)
-- Players can't access it via world interaction, only through code
local hiddenStashId = exports['jaksam_inventory']:registerStash({
    id = "secret_stash",
    label = "Secret Storage",
    maxWeight = 200,
    maxSlots = 30
    -- No coords provided, accessed only programmatically
})

-- Create a private stash (each player gets their own inventory when accessing the stash)
local privateStashId = exports['jaksam_inventory']:registerStash({
    id = "luxury_apartment_stash",
    label = "Personal Safe",
    coords = vector3(300.0, 400.0, 50.0),
    maxWeight = 200,
    maxSlots = 30,
    isPrivate = true
})

-- Create a temporary stash with starting items (won't save to database)
local tempStashId = exports['jaksam_inventory']:registerStash({
    label = "Event Loot Box",
    coords = vector3(500.0, 600.0, 20.0),
    maxWeight = 100,
    maxSlots = 20,
    temporary = true,
    startingItems = {
        {"bread", 5, nil},
        {"water", 3, nil},
        {"money", 1000, nil}
    }
})

-- Create a menu-based stash (runtimeOnly = true by default)
-- Useful for custom UI/menu systems
local virtualStashId = exports['jaksam_inventory']:registerStash({
    id = "player_bank_vault",
    label = "Bank Vault",
    maxWeight = 500,
    maxSlots = 50,
    isPrivate = true
    -- runtimeOnly = true by default, accessed only programmatically
})

-- Open stash programmatically from server (e.g., from a menu or command)
RegisterCommand('openvault', function(source)
    local charId = Framework.getPlayerCharIdentifier(source)
    local stashId = "player_bank_vault_" .. charId
    exports['jaksam_inventory']:forceOpenInventory(source, stashId)
end)

-- Alternative: Open from client-side script
-- exports['jaksam_inventory']:openInventory('stashId')
```

## removeItem
Removes items from an inventory

```lua
exports['jaksam_inventory']:removeItem(inventoryId, itemName, amount, metadata, slotId)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to remove items from
  - Can be a player server ID or inventory ID
- `itemName`: string
  - The name of the item to remove
- `amount`: number
  - How many items to remove
- `metadata`: table (optional)
  - Metadata to match when removing items (if provided, only items with the same metadata AND name will be removed)
- `slotId`: number (optional)
  - Specific slot to remove items from

### Returns

- `success`: boolean
  - true if items were removed successfully
- `resultCode`: string
  - Error message if the operation failed

### Example

```lua
-- Remove 5 bread from player inventory
local success, result = exports['jaksam_inventory']:removeItem(1, 'bread', 5)

-- Remove specific weapon by metadata
local success, result = exports['jaksam_inventory']:removeItem(1, 'weapon_pistol', 1, {
    serial = "ABC123"
})

-- Remove from specific slot
local success, result = exports['jaksam_inventory']:removeItem(1, 'bread', 1, nil, 5)
```

## saveDirtyInventories
Saves all modified inventories to the database

```lua
exports['jaksam_inventory']:saveDirtyInventories()
```

### Parameters
None

### Returns

- `success`: boolean
  - true if all inventories were saved successfully

### Example

```lua
-- Save all modified inventories
exports['jaksam_inventory']:saveDirtyInventories()

-- Good practice to save before server restart
AddEventHandler('onResourceStop', function(resourceName)
    if resourceName == GetCurrentResourceName() then
        exports['jaksam_inventory']:saveDirtyInventories()
    end
end)
```

## saveDirtyInventory
Saves a specific inventory to the database if it has been modified

```lua
exports['jaksam_inventory']:saveDirtyInventory(inventoryId)
```

### Parameters

- `inventoryId`: string | number
  - The ID of the inventory to save

### Returns

- `success`: boolean
  - true if inventory was saved successfully

### Example

```lua
-- Save specific inventory
exports['jaksam_inventory']:saveDirtyInventory('police_stash_1')

-- Save player inventory after important changes
local success = exports['jaksam_inventory']:saveDirtyInventory(1)
if not success then
    print('Failed to save inventory')
end
```

## setInventoryMaxWeight
Sets the maximum weight capacity for an inventory

```lua
exports['jaksam_inventory']:setInventoryMaxWeight(inventoryId, maxWeight)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID to modify
- `maxWeight`: number
  - The new maximum weight capacity

### Returns

- `success`: boolean
  - true if weight was set successfully

### Example

```lua
-- Set player inventory max weight
exports['jaksam_inventory']:setInventoryMaxWeight(1, 100)

-- Set stash max weight
exports['jaksam_inventory']:setInventoryMaxWeight('police_stash_1', 500)
```

## setItemMetadataInSlot
Updates the metadata of an item in a specific inventory slot

```lua
exports['jaksam_inventory']:setItemMetadataInSlot(inventoryId, slotId, metadata)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID containing the item
- `slotId`: number
  - The slot containing the item to update
- `metadata`: table
  - The new metadata to set

### Returns

- `success`: boolean
  - true if metadata was updated successfully
- `resultCode`: string
  - Error message if the operation failed

### Example

```lua
-- Update weapon ammo
exports['jaksam_inventory']:setItemMetadataInSlot(1, 5, {
    serial = "ABC123",
    ammo = 6 -- update ammo count
})

-- Update item durability
exports['jaksam_inventory']:setItemMetadataInSlot(1, 3, {
    durability = 50
})
```

## setDurability
Sets the durability value of an item in a specific inventory slot

```lua
exports['jaksam_inventory']:setDurability(inventoryId, slotId, durability)
```

### Parameters

- `inventoryId`: string | number
  - The inventory ID containing the item
  - Can be a player server ID or inventory ID
- `slotId`: number
  - The slot containing the item to update
- `durability`: number
  - The durability value to set (will be clamped between 0 and 100)

### Returns

- `success`: boolean
  - true if durability was updated successfully
- `resultCode`: string
  - Error message if the operation failed

### Example

```lua
-- Set weapon durability to 75%
local success, result = exports['jaksam_inventory']:setDurability(1, 5, 75)

-- Decrease durability after weapon use
local item = exports['jaksam_inventory']:getItemFromSlot(playerId, slotId)
if item and item.metadata.durability then
    local newDurability = math.max(0, item.metadata.durability - 5)
    exports['jaksam_inventory']:setDurability(playerId, slotId, newDurability)
end

-- Set durability for stash item
exports['jaksam_inventory']:setDurability('police_stash_1', 3, 100)
```