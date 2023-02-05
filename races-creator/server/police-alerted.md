# Police alerted

Triggered when police is alerted server side (only 1 time per alert, instead of on each player for the client side one)

## Event

```lua
RegisterNetEvent("races_creator:alertedPolice", function(coords, message)

end)
```

### Parameters

| Name      | Data Type | Description                                    |
| --------- | --------- | ---------------------------------------------- |
| `coords`  | vector3   | Coordinates where a player tried to sell drugs |
| `message` | string    | Message that would be displayed                |

## Example

```lua
RegisterNetEvent("races_creator:alertedPolice", function(coords, message)
    -- just an example, will NOT work
    TriggerClientEvent("news_script:heistAlert", -1, coords, message)
end)
```

## Where to insert the code?

You can place it in the file `integrations/sv_integrations.lua` of the script, **at the bottom of the file on new lines**
