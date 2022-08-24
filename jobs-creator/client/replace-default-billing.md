# Replace default billing

Triggered when using billing option in F6 actions menu

## Event

```lua
RegisterNetEvent("jobs_creator:actions:createBilling", function()

end)
```

## Example

```lua
-- To place in jobs_creator/integrations/cl_integrations.lua

RegisterNetEvent("jobs_creator:framework:ready", function() 
    -- Disables the default script billing (otherwise there would be 2 billings)
    exports["jobs_creator"]:disableScriptEvent("jobs_creator:actions:createBilling")
end)

RegisterNetEvent("jobs_creator:actions:createBilling", function()
    -- Uses Billing UI event
    TriggerEvent("billing_ui:activateBillingMode")
end)
```

## Where to insert the code?

You can place it in the file `integrations/cl_integrations.lua` of the script, **at the bottom of the file on new lines**
