# Sold by hired dealer

Triggered on the server when a hired dealer sells a drug

## Event

```lua
AddEventHandler("drugs_creator:hiredDealers:itemSold", function(ownerIdentifier, ownerJob, drugName, quantity, totalPrice, territoryName)

end)
```

### Parameters

| Name              | Data Type | Description                                           |
| ----------------- | --------- | ----------------------------------------------------- |
| `ownerIdentifier` | string    | Character identifier of the dealer's owner            |
| `ownerJob`        | string    | Job/gang name of the owner at the time of hiring      |
| `drugName`        | string    | Item ID of the drug sold                              |
| `quantity`        | int       | Quantity sold                                         |
| `totalPrice`      | int       | Total money earned from the sale                      |
| `territoryName`   | string    | Name of the territory where the dealer is located     |

## Example

```lua
AddEventHandler("drugs_creator:hiredDealers:itemSold", function(ownerIdentifier, ownerJob, drugName, quantity, totalPrice, territoryName)
    print(("[Hired Dealer] %s sold %dx %s for $%d in %s (owner: %s)"):format(
        ownerJob, quantity, drugName, totalPrice, territoryName, ownerIdentifier
    ))
end)
```
