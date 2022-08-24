# Toggle current duty status

Trigger to toggle the current duty status of the player

## Event

```lua
TriggerEvent("jobs_creator:toggleCurrentDutyStatus")
```

This will toggle the current duty status of the player (if he was off duty he will be on duty and vice versa)

## Event - alternative

```lua
TriggerEvent("jobs_creator:toggleCurrentDutyStatus", newDutyStatus)
```

This will set the duty status of the player to the new status

## Example

```lua
-- Toggles the current duty status
RegisterCommand("duty", function()
    TriggerEvent("jobs_creator:toggleCurrentDutyStatus")
end, false)
```

## Example - alternative

```lua
RegisterCommand("onduty", function()
    TriggerEvent("jobs_creator:toggleCurrentDutyStatus", true)
end, false)

RegisterCommand("offduty", function()
    TriggerEvent("jobs_creator:toggleCurrentDutyStatus", false)
end, false)
```
