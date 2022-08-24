# Get player allowed actions

To retrieve allowed actions from player's job

## Export

```lua
exports["jobs_creator"]:getAllowedActions()
```

### Return value

| Name      | Data Type | Description                                                                           |
| --------- | --------- | ------------------------------------------------------------------------------------- |
| `actions` | table     | Key value table where key is the action and value it's boolean if it's allowed or not |

## Example

```lua
local actions = exports["jobs_creator"]:getAllowedActions()

print(ESX.DumpTable(actions))

--[[
    Example output
    
    {
        ["canHeal"] = false,
        ["canCheckDrivingLicense"] = false,
        ["canCheckWeaponLicense"] = false,
        ["canRevive"] = false,
        ["canCheckIdentity"] = false,
        ["canRepairVehicles"] = false,
        ["canHandcuff"] = true,
        ["enableBilling"] = true,
        ["canLockpickCars"] = false,
        ["canCheckVehicleOwner"] = false,
        ["canWashVehicles"] = false,
    }
]]
```
