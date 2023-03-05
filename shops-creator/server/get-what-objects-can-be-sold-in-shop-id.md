# Get what objects can be sold in shop ID

This export returns which objects the player can sell in the shop ID, depending on the shop whitelist/blacklist and on if the shop is allowed to manage weapons and/or items

## Export

```lua
local sellableObjects = getSellableObjectsForShopId(playerId, shopId)
```

### Parameters

| Name       | Data Type | Description                                   |
| ---------- | --------- | --------------------------------------------- |
| `playerId` | integer   | The player server ID                          |
| `shopId`   | integer   | The shop ID (the same that's in the database) |

### Output example

```lua
{
	[1] = {
	        ["name"] = "accesscard",
	        ["count"] = 14,
	        ["label"] = "Access Card",
	        ["type"] = "item",
        },
	[2] = {
		["name"] = "bag",
		["count"] = 49,
		["label"] = "Bag",
		["type"] = "item",
	},
	[3] = {
		["name"] = "WEAPON_COMPACTLAUNCHER",
		["count"] = 1,
		["label"] = "Compact launcher",
		["type"] = "weapon",
	},
	[4] = {
		["name"] = "WEAPON_MACHINEPISTOL",
		["count"] = 1,
		["label"] = "Machine pistol",
		["type"] = "weapon",
	}
}
```

## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
