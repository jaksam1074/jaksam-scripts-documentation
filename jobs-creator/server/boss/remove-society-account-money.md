# Remove society account money

To remove money from a society

## Export

```lua
exports["jobs_creator"]:removeSocietyMoney(jobName, amount)
```

### Parameters

| Name      | Data Type | Description               |
| --------- | --------- | ------------------------- |
| `jobName` | string    | Job ID (example police)   |
| `amount`  | integer   | Amount of money to remove |

### Return value

| Name           | Data Type | Description                 |
| -------------- | --------- | --------------------------- |
| `isSuccessful` | boolean   | If money are removed or not |

## Example

```lua
local isSuccessful = exports["jobs_creator"]:removeSocietyMoney("police", 5000)

print(isSuccessful)
```
