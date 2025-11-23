# How to add crafting recipes (drag & drop)

> **Want players to craft items by dragging one item over another? This guide shows you how, step-by-step**

This feature allows players to craft items by dragging a source item over a target item in the same inventory. When the recipe matches, the items are combined and the result is created.

**Note:** This functionality is provided by the `_hooks/sv_craftings.lua` hook. You just need to add your recipes to the `CRAFTING_RECIPES` table.

## How it works

1. Player drags a **source item** over a **target item** in the same inventory
2. The system checks if there's a matching recipe
3. If the recipe matches and quantities are sufficient, the crafting happens
4. Source and/or target items are removed (based on recipe settings)
5. The result item is added to the inventory

## Step-by-step guide

1. Open your server files and navigate to: `jaksam_inventory/_hooks/sv_craftings.lua`
2. Find the `CRAFTING_RECIPES` table (it's near the top of the file)
3. Add your recipe following this format:

```lua
local CRAFTING_RECIPES = {
    ["source_item_name"] = {
        sourceQuantityRequired = 1,        -- How many source items needed
        sourceIsToRemove = true,           -- Remove source item after crafting?
        targetItem = "target_item_name",  -- Name of the target item
        targetQuantity = 1,                -- How many target items needed
        targetIsToRemove = true,           -- Remove target item after crafting?
        resultItem = "result_item_name",  -- Name of the item created
        resultQuantity = 1,                -- How many result items created
    },
}
```

4. Save the file and restart the script/reload the server

That's it! Now players can drag the source item over the target item to craft.

## Recipe properties explained

- **`sourceQuantityRequired`**: How many of the source item are needed for the recipe
- **`sourceIsToRemove`**: Set to `true` if the source item should be removed after crafting, `false` to keep it
- **`targetItem`**: The exact name (as defined in `items.lua`) of the item you drag the source item onto
- **`targetQuantity`**: How many of the target item are needed for the recipe
- **`targetIsToRemove`**: Set to `true` if the target item should be removed after crafting, `false` to keep it
- **`resultItem`**: The exact name (as defined in `items.lua`) of the item that will be created
- **`resultQuantity`**: How many result items will be created

## Examples

### Example 1: Upgrade scope to thermal scope

Combine a wrench with an advanced scope to create a thermal scope:

```lua
["weapon_wrench"] = {
    sourceQuantityRequired = 1,
    sourceIsToRemove = false,              -- Keep the wrench (reusable tool)
    targetItem = "advanced_scope",
    targetQuantity = 1,
    targetIsToRemove = true,               -- Remove the advanced scope
    resultItem = "thermal_scope",
    resultQuantity = 1,
},
```

**How to use:** Drag the wrench over the advanced scope → thermal scope is created, wrench stays, advanced scope is removed.

### Example 2: Combine materials

Combine 2 pieces of wood with 1 nail to create a wooden plank:

```lua
["wood"] = {
    sourceQuantityRequired = 2,
    sourceIsToRemove = true,               -- Remove the 2 wood pieces
    targetItem = "nail",
    targetQuantity = 1,
    targetIsToRemove = true,               -- Remove the nail
    resultItem = "wooden_plank",
    resultQuantity = 1,
},
```

**How to use:** Drag 2 wood items over 1 nail → wooden plank is created, both materials are consumed.

## Important notes

- **Same inventory only**: Crafting only works when both items are in the **same inventory** (you can't drag from player inventory to vehicle inventory)
- **Item names must match**: The `targetItem` and `resultItem` names must exactly match the item names in `_data/items.lua`
- **Quantity checks**: The system automatically checks if you have enough items before crafting
- **Multiple recipes**: You can add as many recipes as you want to the `CRAFTING_RECIPES` table
- **One source, multiple targets**: Each source item can only have one recipe. If you need multiple recipes for the same source item, you'll need to use different source items or create separate crafting systems

