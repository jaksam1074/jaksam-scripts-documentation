# addWeaponToArmory

To add a weapon in a marker ID for a specific player

### Export

```lua
exports["jobs_creator"]:addWeaponToArmory(markerId, playerIdentifier, weaponName, weaponAmmo, weaponComponents, weaponTintIndex)
```

#### Parameters

| Name               | Data Type | Description                |
| ------------------ | --------- | -------------------------- |
| `markerId`         | integer   | The marker ID              |
| `playerIdentifier` | string    | Player identifier          |
| `weaponName`       | string    | Weapon name                |
| `weaponAmmo`       | integer   | Ammo count                 |
| `weaponComponents` | table     | Table of weapon components |
| `weaponTintIndex`  | integer   | Weapon tint index          |

#### Return value

| Name           | Data Type | Description                   |
| -------------- | --------- | ----------------------------- |
| `isSuccessful` | boolean   | If the weapon is added or not |

### Example

```lua
local success = exports["jobs_creator"]:addWeaponToArmory(3, "2570e6efd3671584d7ed05a45cbf4156f782wwac", "WEAPON_PISTOL", 5 {}, 1)

print(success)
```
