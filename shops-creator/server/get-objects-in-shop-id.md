# Get objects in shop ID

This export returns which objects are being sold/bought in shop ID

## Export

```lua
local objectsInShop = getAllObjectFromPlayersShopId(shopId)
```

### Parameters

| Name     | Data Type | Description                                   |
| -------- | --------- | --------------------------------------------- |
| `shopId` | integer   | The shop ID (the same that's in the database) |

### Output example

```lua
{
	[64] = {
		["name"] = "beer",
		["price"] = 5,
		["type"] = "item",
		["quantity"] = 1,
		["label"] = "Beer",
		["method"] = "buy", -- Player can buy the item
		["id"] = 64,
	},
	[65] = {
		["name"] = "weed_seed",
		["price"] = 555,
		["type"] = "item",
		["quantity"] = 5,
		["label"] = "Weed Seed",
		["method"] = "sell",  -- Player can sell the item
		["id"] = 65,
	},
	[63] = {
		["name"] = "accesscard",
		["price"] = 5,
		["type"] = "item",
		["quantity"] = 1,
		["label"] = "Access Card",
		["method"] = "buy", -- Player can buy the item
		["id"] = 63,
	},
}
```

## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
