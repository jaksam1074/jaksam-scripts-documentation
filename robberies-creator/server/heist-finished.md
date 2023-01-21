# Heist finished

Triggered when a heist is completed (the same moment when in the server console it appears "Heist has been completed")

## Event

```lua
RegisterNetEvent("robberies_creator:heist:heistFinished", function(heistId)

end)
```

### Parameters

| Name      | Data Type | Description     |
| --------- | --------- | --------------- |
| `heistId` | integer   | ID of the heist |

## Example

```lua
RegisterNetEvent("robberies_creator:heist:heistFinished", function(heistId)
    -- just an example, will do nothing useful, you may want to retrieve data from database
    
    print("Heist with ID " .. heistId .. " is finished")
end)
```

## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
