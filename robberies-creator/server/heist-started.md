# Heist started

Triggered when a step is finished in the first stage of a not started heist

## Event

```lua
RegisterNetEvent("robberies_creator:heist:heistStarted", function(heistId)

end)
```

### Parameters

| Name      | Data Type | Description     |
| --------- | --------- | --------------- |
| `heistId` | integer   | ID of the heist |

## Example

```lua
RegisterNetEvent("robberies_creator:heist:heistStarted", function(heistId)
    -- just an example, will do nothing useful, you may want to retrieve data from database
    
    print("Heist with ID " .. heistId .. " has just started")
end)
```

## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
