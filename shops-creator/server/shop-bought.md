# Shop bought

Triggered after a player buys a player owned shop

## Event

```lua
RegisterNetEvent("shops_creator:playersShops:shopBought", function(shopId, ownerIdentifier)

end)
```

### Parameters

| Name         | Data Type | Description                                   |
| ------------ | --------- | --------------------------------------------- |
| `shopId`     | integer   | The shop ID (the same that's in the database) |
| `identifier` | string    | The identifier of the new owner               |



## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
