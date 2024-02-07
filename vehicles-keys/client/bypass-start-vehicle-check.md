# Bypass start vehicle check

You can bypass the start vehicle check by setting the state bag `canAlwaysStart to true`

## Example

<pre class="language-lua"><code class="lang-lua"><strong>-- This command will make the player bypass the current vehicle start conditions
</strong><strong>RegisterCommand("startbypass", function()
</strong>    local plyPed = PlayerPedId()
    local plyVeh = GetVehiclePedIsIn(plyPed)
    
    Entity(plyVeh).state.canAlwaysStart = true
end)
</code></pre>

Note: the bypass will apply when you enter the vehicle, **after** that the bypass is enabled
