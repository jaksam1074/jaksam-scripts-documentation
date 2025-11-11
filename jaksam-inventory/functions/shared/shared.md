# Shared functions
Here there are built-in exports of jaksam's inventory, works both on server and client

## getStaticItemsList
Returns the list of all items in the inventory

```lua
exports['jaksam_inventory']:getStaticItemsList()
```

### Returns
- `items`: table
  - The list of items, key is the item name, value is item information (label, maxStack, weight, stackable, description, rarity, type, etc.)

### Example

```lua
-- Get the list of items
local items = exports['jaksam_inventory']:getStaticItemsList()
local weaponsCount = 0
for itemName, item in pairs(items) do
    if item.type == 'weapon' then
        weaponsCount = weaponsCount + 1
    end
end
print("There are in total " .. weaponsCount .. " registered weapons in the inventory")
```

## getStaticItem
Gets generic item information from the inventory, like weight, stackable, description, label, etc.

```lua
exports['jaksam_inventory']:getStaticItem(itemName)
```

### Parameters
- `itemName`: string
  - The name of the item to get

### Returns
- `item`: table
  - The item information, if the item is not found, it will return nil

### Example

```lua
-- Get the information of the item "bread"
local item = exports['jaksam_inventory']:getStaticItem('bread')
print(item.label) -- Bread
print(item.weight) -- 1.0
print(item.stackable) -- true
print(item.description) -- A bread
print(item.maxStack) -- 100
print(item.rarity) -- common
print(item.type) -- item|container|ammo|currency
```

## getItemLabel
Gets only the label (display name) of an item. This is a simpler and faster alternative to `getStaticItem` when you only need the item's label

```lua
exports['jaksam_inventory']:getItemLabel(itemName)
```

### Parameters
- `itemName`: string
  - The name of the item to get the label for

### Returns
- `label`: string|nil
  - The label (display name) of the item, or nil if the item is not found

### Example

```lua
-- Get the label of the item "bread"
local label = exports['jaksam_inventory']:getItemLabel('bread')
print(label) -- Bread

-- Item not found returns nil
local notFound = exports['jaksam_inventory']:getItemLabel('invalid_item')
print(notFound) -- nil
```