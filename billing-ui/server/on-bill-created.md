# On bill created

This event is triggered after a bill is created

## Event

```lua
RegisterNetEvent("billing_ui:onBillCreated", function(billId, senderIdentfier, targetIdentifier, amount, date, unixDate)

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
