# Admin Commands

All admin commands require ACE permission (Use /inventory to see if you have it)

## `/inventory`

Opens the admin menu to manage items, shops, stashes, view statistics, etc.

## `/giveitem <inventoryId|playerId|'me'> <itemName> <amount> [slotId]`

Give items to a player or inventory

```lua
/giveitem me bread 10       -- Give 10 bread to yourself
/giveitem 1 water 5          -- Give 5 water to player 1
/giveitem stash_police weapon_pistol 1 3 -- Give 1 weapon_pistol to stash_police in slot 3
```

## `/removeitem <inventoryId> <itemName> <amount> [slotId]`

Remove items from a player or inventory

```lua
/removeitem 1 bread 10          -- Remove 10 bread from player 1's inventory
/removeitem stash_police weapon_pistol 1 -- Remove 1 weapon_pistol from stash_police
```

## `/clearinventory [inventoryId] [excludedItemName]`

Clear all items from an inventory. If `inventoryId` is empty, clears your own inventory. You can also exclude an item from clearing

```lua
/clearinventory          -- Clear your inventory
/clearinventory 1        -- Clear player 1's inventory
/clearinventory 2 phone  -- Clear player 2's inventory but keep phone
```

## `/openinventory <targetPlayerId>`

Open another player's inventory

```lua
/openinventory 1          -- Open player 1's inventory
```

## `/saveinventories`

Force save all modified inventories to database