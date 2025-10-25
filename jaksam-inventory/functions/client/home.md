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
