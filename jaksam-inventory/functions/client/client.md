# Client functions
Here there are built-in exports of jaksam's inventory that can be used client-side

## getTotalItemAmount
Gets the total amount of a specific item in the player's inventory

```lua
exports['jaksam_inventory']:getTotalItemAmount(itemName, metadata)
```

### Parameters

- `itemName`: string
  - The name of the item to count
- `metadata`: table (optional)
  - Metadata to match against when counting (if provided, only items with the same metadata AND name will be counted)

### Returns

- `totalAmount`: number
  - Total amount of the item in the player's inventory

### Example

```lua
-- Get total amount of bread
local breadCount = exports['jaksam_inventory']:getTotalItemAmount('bread')

-- Get amount of specific weapon by serial
local weaponCount = exports['jaksam_inventory']:getTotalItemAmount('weapon_pistol', {
    serial = "ABC123"
})
```

## openInventory
Opens an inventory alongside the player's inventory

```lua
exports['jaksam_inventory']:openInventory(inventoryId)
```

### Parameters

- `inventoryId`: string
  - The ID of the inventory to open

### Returns
None - Opens the inventory UI if successful

### Example

```lua
-- Open a stash inventory
exports['jaksam_inventory']:openInventory('police_stash_1')

-- Open a trunk inventory
exports['jaksam_inventory']:openInventory('car_trunk_123')
```

## getInventory
Gets the player's self inventory

```lua
exports['jaksam_inventory']:getInventory()
```

### Parameters
None

### Returns
- `inventory`: table
  - The player's self inventory

### Example

```lua
-- Get the player's self inventory
local inventory = exports['jaksam_inventory']:getInventory()

print(json.encode(inventory, {indent = true}))
--[[
{
    "id": "SIV35463",
    "limits": {
        "maxSlots": 20,
        "maxWeight": 30
    },
    "items": {
        "SLOT-3": {
            "name": "money",
            "amount": 4402
        },
        "SLOT-1": {
            "name": "weapon_advancedrifle",
            "metadata": {
                "serial": "TSK-24895-LFN"
            },
            "amount": 1
        },
    },
    "label": "Inventory",
    "totalWeight": 21.0,
}
]]
```

## getItemByName
Returns the first item found in the player's self inventory by name (order not guaranteed)

```lua
exports['jaksam_inventory']:getItemByName(itemName)
```

### Parameters
None

### Returns
- `item`: table
  - The item found in the player's self inventory
- `slotId`: number
  - The slot ID of the item in the player's self inventory

### Example

```lua
-- Get the first item by name
local item, slotId = exports['jaksam_inventory']:getItemByName('weapon_advancedrifle')

print(json.encode(item, {indent = true}), "SLOT ID: " .. slotId)
--[[
{
    "name": "weapon_advancedrifle",
    "metadata": {
        "serial": "TSK-24895-LFN"
    },
    "amount": 1
}
SLOT ID: 1
```

## getItemFromSlot
Gets an item from a specific slot in the player's inventory

```lua
exports['jaksam_inventory']:getItemFromSlot(slotId)
```

### Parameters

- `slotId`: number
  - The slot number to get the item from (in the player's inventory)

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
local item = exports['jaksam_inventory']:getItemFromSlot(5)

if item then
    print('Item name:', item.name)
    print('Amount:', item.amount)
    if item.metadata then
        print('Metadata:', json.encode(item.metadata))
    end
else
    print('Slot 5 is empty')
end

-- Check if a specific slot has a weapon
local slotItem = exports['jaksam_inventory']:getItemFromSlot(1)
if slotItem then
  local staticItem = exports['jaksam_inventory']:getStaticItem(slotItem.name)
  if staticItem and staticItem.type == 'weapon' then
    print('Found weapon in slot 1:', slotItem.name)
  end
end
```

## showHotbar
Shows the hotbar UI with the first 5 slots of the player's inventory

```lua
exports['jaksam_inventory']:showHotbar()
```

### Parameters
None

### Returns
None - Shows the hotbar UI which automatically hides after 2 seconds

### Example

```lua
-- Show hotbar
exports['jaksam_inventory']:showHotbar()

-- Show hotbar after receiving an item
AddEventHandler('myScript:itemReceived', function()
    exports['jaksam_inventory']:showHotbar()
end)
```

Notes:
- The hotbar shows slots 1-5 from the player's inventory
- If `config.dynamicHotbar` is true, empty slots at the end are hidden
- The hotbar automatically hides after 2 seconds
- Multiple calls reset the hide timer

## dequipWeapon
Deequips the currently equipped weapon

```lua
exports['jaksam_inventory']:dequipWeapon(skipSync)
```

### Parameters
- `skipSync`: boolean (optional)
  - If true, the weapon will be deequipped without syncing the ammo to the server

### Returns
None - Deequips the currently equipped weapon

### Example

```lua
-- Deequip weapon
exports['jaksam_inventory']:dequipWeapon()

-- Deequip weapon without syncing the ammo to the server
exports['jaksam_inventory']:dequipWeapon(true)
```