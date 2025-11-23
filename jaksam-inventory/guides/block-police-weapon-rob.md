# How to prevent police weapons from being stolen

> **Want to make sure only police officers can move police weapons to their inventory? This guide shows you how, step-by-step**

This feature prevents non-police players from moving police weapons into their personal inventory. If a player tries to steal a police weapon, they'll get an error message and the transfer will be blocked

**Note:** This functionality is automatically provided by the `_hooks/sv_policeonly.lua` hook (in case you want to edit it). You just need to mark your weapons as police-only

## Step-by-step guide

1. Open your server files and navigate to: `jaksam_inventory/_data/items.lua`
2. Find the weapon item you want to protect (or create it if it doesn't exist)
3. Add `policeOnly = true` to the item definition
4. Save the file and restart the script/reload the server

That's it! Now only players with the "police" job can move that weapon to their personal inventory

## Examples

### Example 1: Combat Pistol

```lua
['WEAPON_COMBATPISTOL'] = {
    label = 'Combat Pistol',
    weight = 1.0,
    stackable = false,
    close = true,
    description = 'A combat pistol',
    type = 'weapon',
    ammo = 'ammo_9mm',
    throwableOptions = {
        model = nil,
        coords = {x = 0.08, y = 0.03, z = -0.06},
        rot = {x = -25.45, y = -3.76, z = 49.99}
    },
    policeOnly = true  -- Only police can move this weapon
},
```

### Example 2: Stun Gun

```lua
['WEAPON_STUNGUN'] = {
    label = 'Stun Gun',
    weight = 1.0,
    stackable = false,
    close = true,
    description = 'A police stun gun',
    type = 'weapon',
    policeOnly = true  -- Only police can move this weapon
},
```

## How it works

The `sv_policeonly.lua` hook automatically checks every time someone tries to move a weapon with `policeOnly = true` to a player inventory. If the player doesn't have the "police" job, the transfer is blocked and they see an error message

**Important:** This only blocks transfers to **player inventories**. Police weapons can still be moved between other inventory types (like storage, vehicles, etc.) by anyone