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
if(not exports["jobs_creator"]:isPlayerHandcuffed())then
    print("You are not handcuffed")
else
    print("You are handcuffed")
end
```

## Where to insert the code?

You can place the code in any client file of your scripts
