# Replacing default events names

In case your server uses different event names than the default ones, you can edit those names in `jobs_creator/integrations/cl_integrations.lua` **and** `jobs_creator/integrations/sv_integrations.lua`

Example of default ones:

```lua
EXTERNAL_EVENTS_NAMES = {
    ["esx:getSharedObject"] = nil,
    
    ["esx_skin:save"] = "esx_skin:save",

    ["esx_billing:sendBill"] = "esx_billing:sendBill",

    ["jsfour-idcard:open"] = "jsfour-idcard:open",

    ["esx_license:removeLicense"] = "esx_license:removeLicense",
    ["esx_license:addLicense"] = "esx_license:addLicense",
}
```

\
Example of edited ones:

```lua
EXTERNAL_EVENTS_NAMES = {
    ["esx:getSharedObject"] = "gamemode:getSharedObject",
    
    ["esx_skin:save"] = "my_skin_script:save",

    ["esx_billing:sendBill"] = "billing_ui:sendBill",

    ["jsfour-idcard:open"] = "jsfour-idcard:open",

    ["esx_license:removeLicense"] = "licenses:removeLicense",
    ["esx_license:addLicense"] = "licenses:addLicense",
}
```
