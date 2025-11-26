# How to show metadata to players
Showing specific metadata to players is easy. First of all, you'll need to know what is the metadata key you want to show, to do so, you can enable "Debug mode" in the `/inventory` settings menu, then hover the item you want to see the metadata of

<table>
<tr>
<td><img src="../../.gitbook/assets/settings_debug_screenshot.png" alt="Item debug settings screenshot" width="700"></td>
<td><img src="../../.gitbook/assets/item_debug_metadata.png" alt="Item debug metadata screenshot"></td>
</tr>
</table>

## Adding it to a single item
To show to players the metadata of a single item, you can add and adapt this code in the single item definition, in `jaksam_inventory/_data/items.lua` file:

```lua
displayFields = {
    { field = 'YOUR_METADATA_KEY_HERE', label = 'TEXT YOU WANT HERE: ${value}'}, -- Random example
    { field = 'ammo', label = 'Ammo: ${value}'}, -- Useful on weapons (already built in by default)
    { field = 'plate', label = 'Plate: ${value}'}, -- Useful on carkeys
},

```

<img src="../../.gitbook/assets/single_item_display_fields_example.png" alt="Single item display fields example">

## Adding it to all item type
To show to players the metadata of an entire item type, it's 100% the same method, but place it in the `Script.defaultsByType` table, in `jaksam_inventory/_data/defaults.lua` file

## Optional: Making metadata values look nicer
Sometimes you want to show metadata in a prettier way to players. For example, instead of showing "weapon_pistol", you want to show "Pistol". This is where formatters come in!

A formatter is like a translator:
- It takes the original value (e.g. "weapon_pistol") 
- Converts it to something nicer (e.g. "Pistol")

You can use built-in formatters or create your own custom ones in `jaksam_inventory/_data/formatter.lua`. Here's how to use them:

```lua
displayFields = {
    { field = 'item', label = 'Label: ${value}', formatterId = "itemNameToLabel"}, -- An example with built in formatter
},
```

# How to set default metadata for items
Want items to have certain metadata values when they're first created? For example, maybe you want new weapons to start with 50% durability. Here's how to do it:

1. Type `/inventory` in-game to open the admin menu
2. Find and click on the item you want to edit
3. Click on the "metadata" tab
4. Set the metadata values you want

## Advanced - Using templates for dynamic metadata
Sometimes you want metadata that changes based on certain conditions. For this, you can use templates:

1. Go to the same metadata tab in the item editor
2. Change the metadata type to `template` 
3. Either:
   - Select an existing template, or
   - Create your own template in `jaksam_inventory/_data/metadata_templates.lua`

Templates let you create metadata that updates automatically based on rules you define!

### Example
Some examples of what you can do with dynamic metadata templates:
- Assign to a player Identification Card, his name, birth date, height, etc.
- Assign a random durability to a weapon
- Assign the creation date to an item (the first time the item is created)

