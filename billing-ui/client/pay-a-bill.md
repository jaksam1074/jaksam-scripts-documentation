# Pay a bill

Trigger to pay a bill ID properly, you can use this from external scripts

## Event

```lua
TriggerServerEvent("billing_ui:payInvoice", billId)
```

### Parameters

| Name     | Data Type | Description                                               |
| -------- | --------- | --------------------------------------------------------- |
| `billId` | integer   | The bill ID (the ID is from the database table `billing`) |
