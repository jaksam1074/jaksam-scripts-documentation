# Refresh bill

This export will refresh the specified bill ID, so if you edit the values in the database, you can use this export so the script won't require a restart to see it

Note: if you have to delete a bill, use the [delete-bill.md](delete-bill.md "mention")export

## Export

```lua
exports["billing_ui"]:refreshBillId(billId)
```

### Parameters

| Name     | Data Type | Description                                              |
| -------- | --------- | -------------------------------------------------------- |
| `billId` | integer   | The bill ID you can find in the database table `billing` |

## Example

```lua
-- Example command /refreshBillId 51
RegisterCommand("refreshBillId", function(playerId, args)
    local billId = tonumber(args[1])
    exports["billing_ui"]:refreshBillId(billId)
end)
```
