# Get owned plates of local player

This export can be get all the owned plates of **the local player**&#x20;

## Export

<pre class="language-lua"><code class="lang-lua"><strong>local ownedPlates = exports["vehicles_keys"]:getOwnedVehiclePlates()
</strong></code></pre>

### Return

A table containing all the owned plates with the following format

```lua
{
    ["ABC123"] = {
        type = "owned",
        model = -35726841
    },
    
    ["BCD473"] = {
        type = "temporary",
        model = -55726841
    },
}
```
