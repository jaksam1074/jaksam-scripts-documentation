# Player shop bought object

Triggered after a player buys an object from a player owned shop

## Event

```lua
RegisterNetEvent("shops_creator:playersShops:boughtObject", function(playerId, shopId, objectId, quantity)

end)
```

### Parameters

| Name       | Data Type | Description                                   |
| ---------- | --------- | --------------------------------------------- |
| `playerId` | integer   | The player ID who bought the object           |
| `shopId`   | integer   | The shop ID (the same that's in the database) |
| `objectId` | integer   | The object ID that was bought                 |
| `quantity` | integer   | The quantity of items bought                  |

## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
