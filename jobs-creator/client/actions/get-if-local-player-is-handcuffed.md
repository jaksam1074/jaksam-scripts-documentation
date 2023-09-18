# Get if local player is handcuffed

Returns if the **local** client/player is handcuffed

## Export

```lua
exports["jobs_creator"]:isPlayerHandcuffed()
```

### Return value

| Name           | Data Type | Description                                                                 |
| -------------- | --------- | --------------------------------------------------------------------------- |
| `isHandcuffed` | boolean   | true if the player is handcuffed. false if the player is **not** handcuffed |

## Example

```lua
-- This code will continuously check if the local (self) player is handcuffed
-- If so, specified controls will be disabled
Citizen.CreateThread(function() 
    while true do
        Citizen.Wait(0)
        
        if(exports["jobs_creator"]:isPlayerHandcuffed())then
            DisableControlAction(0, 22, true) -- Disable jump
        end       
    end
end)
```

## Where to insert the code?

You can place the code in any client file of your scripts
