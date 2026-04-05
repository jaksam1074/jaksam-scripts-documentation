# Ownership changed

Triggered on the server when a territory changes owner

## Event

```lua
AddEventHandler("drugs_creator:territories:ownershipChanged", function(territoryName, newOwner, previousOwner)

end)
```

### Parameters

| Name             | Data Type    | Description                                           |
| ---------------- | ------------ | ----------------------------------------------------- |
| `territoryName`  | string       | The name of the territory that changed owner          |
| `newOwner`       | string / nil | The job/gang name of the new owner, or nil if lost    |
| `previousOwner`  | string / nil | The job/gang name of the previous owner, or nil       |

## Example

```lua
AddEventHandler("drugs_creator:territories:ownershipChanged", function(territoryName, newOwner, previousOwner)
    if newOwner then
        print(("%s is now owned by %s (was: %s)"):format(territoryName, newOwner, previousOwner or "nobody"))
    else
        print(("%s has been lost by %s"):format(territoryName, previousOwner or "unknown"))
    end
end)
```
