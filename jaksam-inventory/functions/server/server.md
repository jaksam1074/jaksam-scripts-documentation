# Compatibility
Included in the script, there will be compatibility for many exports of some other inventories, as es_extended, qb-inventory and ox_inventory. Despite it's not the preferred way, to make compatibility easy for you, you can often replace old exports by just using the script name, keeping the same parameters

Example:
```lua
-- Before
local success = exports['ox_inventory']:AddItem(inventoryId, itemName, amount, metadata, slotId)
-- After
local success = exports['jaksam_inventory']:AddItem(inventoryId, itemName, amount, metadata, slotId)
```

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
  - Callback receives: playerId

### Returns

- `success`: boolean
  - true if registration was successful

### Example

```lua
-- Register usable item
exports['jaksam_inventory']:registerUsableItem('bread', function(playerId)
    -- Heal player when bread is used
    local plyPed = GetPlayerPed(playerId)
    local health = GetEntityHealth(plyPed)
    SetEntityHealth(plyPed, math.min(health + 20, 200))
end)
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