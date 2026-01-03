# Compatibility
This script works with other popular inventory systems, like es_extended, qb-inventory, and ox_inventory

For ESX and QBCore functions, the setup is done automatically. But, if you want to keep using exports from ox_inventory or qb-inventory for compatibility, you need to turn on this option in the file: `jaksam_inventory/integrations/sv_integrations.lua`

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

## setHotbarDisabled
Enables or disables the hotbar functionality. Useful for example during minigames. Don't forget to re-enable the hotbar when finished

```lua
exports['jaksam_inventory']:setHotbarDisabled(disabled)
```

### Parameters

- `disabled`: boolean
  - If true, the hotbar will be disabled and `showHotbar()` calls will be ignored
  - If false, the hotbar will be enabled and will work normally

### Returns
None

### Example

```lua
-- Disable the hotbar
exports['jaksam_inventory']:setHotbarDisabled(true)

-- Enable the hotbar
exports['jaksam_inventory']:setHotbarDisabled(false)

-- Disable hotbar during a cutscene
exports['jaksam_inventory']:setHotbarDisabled(true)
-- ... cutscene code ...
exports['jaksam_inventory']:setHotbarDisabled(false)
```

## setHotkeysEnabled
Enables or disables the hotkeys functionality (slots 1-5). Useful for example during minigames or cutscenes. Don't forget to re-enable the hotkeys when finished

```lua
exports['jaksam_inventory']:setHotkeysEnabled(enabled)
```

### Parameters

- `enabled`: boolean
  - If true, the hotkeys will be enabled and will work normally
  - If false, the hotkeys will be disabled and pressing 1-5 will be ignored

### Returns
None

### Example

```lua
-- Disable the hotkeys
exports['jaksam_inventory']:setHotkeysEnabled(false)

-- Enable the hotkeys
exports['jaksam_inventory']:setHotkeysEnabled(true)

-- Disable hotkeys during a minigame
exports['jaksam_inventory']:setHotkeysEnabled(false)
-- ... minigame code ...
exports['jaksam_inventory']:setHotkeysEnabled(true)
```

## areHotkeysEnabled
Returns whether the hotkeys are currently enabled or disabled

```lua
exports['jaksam_inventory']:areHotkeysEnabled()
```

### Parameters
None

### Returns

- `enabled`: boolean
  - True if hotkeys are enabled, false if disabled

### Example

```lua
-- Check if hotkeys are enabled
local enabled = exports['jaksam_inventory']:areHotkeysEnabled()

if enabled then
    print('Hotkeys are enabled')
else
    print('Hotkeys are disabled')
end

-- Toggle hotkeys
local currentState = exports['jaksam_inventory']:areHotkeysEnabled()
exports['jaksam_inventory']:setHotkeysEnabled(not currentState)
```

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

## setWeaponWheel
Enables or disables the weapon wheel and related weapon settings. Useful for minigames where you want the GTA 5 weapon wheel. Note that this function will prevent using weapons from the inventory, it's mainly for FFA minigames

```lua
exports['jaksam_inventory']:setWeaponWheel(state)
```

### Parameters

- `state`: boolean | nil
  - If true, the weapon wheel will be enabled
  - If false, the weapon wheel will be disabled and weapons cannot be auto-swapped
  - If nil, uses the current internal state

### Returns
None - Automatically deequips the current weapon when called

### Example

```lua
-- Disable weapon wheel
exports['jaksam_inventory']:setWeaponWheel(false)

-- Enable weapon wheel
exports['jaksam_inventory']:setWeaponWheel(true)

-- Disable weapon wheel during FFA minigame
exports['jaksam_inventory']:setWeaponWheel(false)
-- ... minigame code ...
exports['jaksam_inventory']:setWeaponWheel(true)
```

## registerActionButton
Registers a custom action button in the inventory UI toolbar. Action buttons appear on the right side of the inventory and can trigger any custom logic when clicked

For a complete guide with images and examples, see the [Action Buttons Guide](../guides/action-buttons.md).

```lua
exports['jaksam_inventory']:registerActionButton(id, icon, tooltip, onClick, visible)
```

### Parameters

- `id`: string
  - Unique identifier for the button. Used to reference the button when showing/hiding/unregistering
- `icon`: string
  - Bootstrap Icons class name (e.g. "bi-shield-x", "bi-car-front-fill"). Find icons at https://icons.getbootstrap.com/
- `tooltip`: string | nil
  - Tooltip text shown when hovering the button. Can be nil for no tooltip
- `onClick`: function
  - Callback function executed when the button is clicked
- `visible`: boolean | nil
  - Whether the button should be visible initially. Default: true

### Returns
None

### Example

```lua
-- Register a simple action button
exports['jaksam_inventory']:registerActionButton(
    'my_custom_button',
    'bi-star-fill',
    'My Custom Action',
    function()
        print('Button clicked!')
        -- Your custom logic here
    end
)

-- Register a hidden button (to show later based on conditions)
exports['jaksam_inventory']:registerActionButton(
    'police_actions',
    'bi-shield-check',
    'Police Actions',
    function()
        TriggerEvent('myPoliceScript:openMenu')
    end,
    false -- hidden by default
)
```

## unregisterActionButton
Removes a previously registered action button from the inventory UI

```lua
exports['jaksam_inventory']:unregisterActionButton(id)
```

### Parameters

- `id`: string
  - The unique identifier of the button to remove (same id used in registerActionButton)

### Returns
None

### Example

```lua
-- Unregister a button when no longer needed
exports['jaksam_inventory']:unregisterActionButton('my_custom_button')

-- Unregister when player leaves a job
AddEventHandler('esx:setJob', function(job)
    if job.name ~= 'police' then
        exports['jaksam_inventory']:unregisterActionButton('police_actions')
    end
end)
```

## showActionButton
Makes a previously hidden action button visible in the inventory UI

```lua
exports['jaksam_inventory']:showActionButton(id)
```

### Parameters

- `id`: string
  - The unique identifier of the button to show

### Returns
None

### Example

```lua
-- Show a button that was registered as hidden
exports['jaksam_inventory']:showActionButton('police_actions')

-- Show button when player gets a specific job
AddEventHandler('esx:setJob', function(job)
    if job.name == 'police' then
        exports['jaksam_inventory']:showActionButton('police_actions')
    end
end)
```

## hideActionButton
Hides an action button from the inventory UI without removing it

```lua
exports['jaksam_inventory']:hideActionButton(id)
```

### Parameters

- `id`: string
  - The unique identifier of the button to hide

### Returns
None

### Example

```lua
-- Hide a button temporarily
exports['jaksam_inventory']:hideActionButton('police_actions')

-- Hide button when player is off-duty
AddEventHandler('esx:setJob', function(job)
    if job.name ~= 'police' then
        exports['jaksam_inventory']:hideActionButton('police_actions')
    end
end)
```