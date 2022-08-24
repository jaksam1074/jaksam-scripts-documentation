# Get all armory weapons

To get a list of all weapons stored in a specific armory ID.

### Export

```lua
exports["jobs_creator"]:getAllArmoryWeapons(markerId)
```

#### Parameters

| Name       | Data Type | Description   |
| ---------- | --------- | ------------- |
| `markerId` | integer   | The marker ID |

#### Return value

| Name            | Data Type | Description                                 |
| --------------- | --------- | ------------------------------------------- |
| `armoryWeapons` | table     | List of all weapons contained in the marker |

### Example

```lua
local allWeapons = getAllArmoryWeapons(markerId)

print("All players weapons in that armory")
print(ESX.DumpTable(allWeapons))
```
