# Shared functions
Here there are built-in exports of jaksam's inventory, works both on server and client

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
