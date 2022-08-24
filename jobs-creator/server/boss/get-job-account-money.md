# Get job account money

To get a list of weapons of a player stored in a specific armory ID.

## Export

```lua
exports["jobs_creator"]:getJobAccountMoney(jobName)
```

### Parameters

| Name      | Data Type | Description             |
| --------- | --------- | ----------------------- |
| `jobName` | string    | Job ID (example police) |

### Return value

| Name           | Data Type | Description                     |
| -------------- | --------- | ------------------------------- |
| `accountMoney` | integer   | Money stored in society account |

## Example

```lua
local jobMoney = exports["jobs_creator"]:getJobAccountMoney("gang_job")

print(jobMoney)
```
