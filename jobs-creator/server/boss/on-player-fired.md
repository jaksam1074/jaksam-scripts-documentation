# On player fired

Triggered when a player has been fired from a job

## Event

```lua
RegisterNetEvent("jobs_creator:boss:employeeFired", function(employeeIdentifier, jobName)

end)
```

### Parameters

| Name                 | Data Type | Description                                     |
| -------------------- | --------- | ----------------------------------------------- |
| `employeeIdentifier` | string    | Player's character identifier                   |
| `jobName`            | string    | The job ID which the player has been fired from |
