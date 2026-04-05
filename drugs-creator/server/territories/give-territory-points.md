# Give territory points

Adds points to a faction in a territory from an external script

## Export

```lua
exports["drugs_creator"]:giveTerritoryPoints(territory, job, amount)
```

### Parameters

| Name        | Data Type | Description                                                                 |
| ----------- | --------- | --------------------------------------------------------------------------- |
| `territory` | string    | Territory name, or `"*"` to target all territories                          |
| `job`       | string    | Job/gang name to give points to, or `"*"` to target all configured factions |
| `amount`    | int       | Number of points to add (must be > 0)                                       |

## Example

```lua
-- Give 2 points to "ballas" in "RANCHO"
exports["drugs_creator"]:giveTerritoryPoints("RANCHO", "ballas", 2)

-- Give 3 points to all factions in all territories
exports["drugs_creator"]:giveTerritoryPoints("*", "*", 3)
```
