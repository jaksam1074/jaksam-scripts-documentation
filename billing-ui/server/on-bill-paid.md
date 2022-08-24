# On bill paid

This event is triggered after a bill is paid

## Event

```lua
RegisterNetEvent("billing_ui:onBillPaid", function(billId, senderIdentfier, targetIdentifier, amount, date, unixDate)

end)
```

### Parameters

| Name               | Data Type | Description                                 |
| ------------------ | --------- | ------------------------------------------- |
| `billId`           | integer   | The bill ID                                 |
| `senderIdentfier`  | string    | Bill sender identifier                      |
| `targetIdentifier` | string    | Bill receiver identifier                    |
| `amount`           | integer   | Amount of the bill paid                     |
| `date`             | integer   | Date when bill was created in readable form |
| `unixDate`         | integer   | Date in unix time                           |
