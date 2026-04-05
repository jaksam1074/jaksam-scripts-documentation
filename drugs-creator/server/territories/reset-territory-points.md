# Reset territory points

Resets points for a faction in a territory (sets to 0). Ownership is recalculated after the reset

## Export

```lua
exports["drugs_creator"]:resetTerritoryPoints(territory, job)
```

### Parameters

| Name        | Data Type | Description                                                                    |
| ----------- | --------- | ------------------------------------------------------------------------------ |
| `territory` | string    | Territory name, or `"*"` to target all territories                             |
| `job`       | string    | Job/gang name to reset, or `"*"` to target all configured factions             |

## Example

```lua
-- Reset points for "ballas" in "RANCHO"
exports["drugs_creator"]:resetTerritoryPoints("RANCHO", "ballas")

-- Full reset: all factions in all territories
exports["drugs_creator"]:resetTerritoryPoints("*", "*")
```
