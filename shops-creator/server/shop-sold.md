# Shop sold

Triggered after a player sells a player owned shop

## Event

```lua
RegisterNetEvent("shops_creator:playersShops:shopSold", function(shopId, ownerIdentifier)

end)
```

### Parameters

| Name         | Data Type | Description                                   |
| ------------ | --------- | --------------------------------------------- |
| `shopId`     | integer   | The shop ID (the same that's in the database) |
| `identifier` | string    | The identifier of the old owner               |



## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
