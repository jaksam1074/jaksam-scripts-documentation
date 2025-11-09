# Adding custom weapon attachments/components

In GTA V, each weapon has different component IDs for the same attachment type. For example, a suppressor for a Pistol uses `COMPONENT_AT_PI_SUPP`, while a Combat Pistol uses `COMPONENT_AT_PI_SUPP_02`

**The inventory system simplifies this:** You can create ONE item (like "suppressor") that automatically works with all compatible weapons by mapping multiple component IDs to it

## Step-by-step guide

### Step 1: Check if the item exists

First, check if an item for your attachment type already exists. For example, if you want to add a modded suppressor:
- Look in your inventory or use `/inventory` to see if a "suppressor" item already exists
- If it exists, note down its **item ID** (not the label)

### Step 2A: If the item already exists

Simply open `jaksam_inventory/_data/components.lua` and add your modded component ID to the existing item:

```lua
["suppressor"] = {
    "COMPONENT_AT_PI_SUPP",
    "COMPONENT_AT_PI_SUPP_02",
    "YOUR_MODDED_COMPONENT_ID_HERE",  -- Add your new component ID here, don't forget to add a comma after each ID
},
```

### Step 2B: If the item doesn't exist

1. Type `/inventory` in-game to open the admin menu
2. Create a new item with these settings:
   - **Item ID**: Choose a clear name (e.g., `red_dot_sight`)
   - **Item Type**: **IMPORTANT!** Select the correct type:
     - `attachment_scope` - For scopes and sights
     - `attachment_barrel` - For suppressors, muzzle brakes, compensators
     - `attachment_grip` - For grips and foregrips
     - `attachment_flashlight` - For flashlights and tactical lights
     - `attachment_magazine` - For extended magazines
     - etc
   - **Other settings**: Set weight, label, description, and image as you prefer

3. Note down the **item ID** you created

4. Open `jaksam_inventory/_data/components.lua` and add your mapping:

```lua
["your_item_id_here"] = {
    "YOUR_COMPONENT_ID_1",
    "YOUR_COMPONENT_ID_2",
    -- Add all component IDs this item should cover
},
```

## Example

Let's say you have a modded weapon with a custom scope component `COMPONENT_MODDED_SCOPE_01`:

**Option A - Item exists:**
```lua
["scope"] = {
    "COMPONENT_AT_SCOPE_MACRO",
    "COMPONENT_AT_SCOPE_SMALL",
    "COMPONENT_MODDED_SCOPE_01",  -- Added
},
```

**Option B - Create new item `custom_scope` via `/inventory`, then:**
```lua
["custom_scope"] = {
    "COMPONENT_MODDED_SCOPE_01",
    "COMPONENT_MODDED_SCOPE_02",
},
```

**That's it!** The system will automatically apply the correct component based on the weapon

