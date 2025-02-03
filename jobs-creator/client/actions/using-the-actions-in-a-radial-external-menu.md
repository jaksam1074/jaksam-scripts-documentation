---
description: >-
  You can use the actions in any external menu, here there are the triggers you
  can use from external scripts
---

# Using the actions in a radial/external menu

{% hint style="warning" %}
Make sure that the job has the actions enabled in Jobs Creator settings of that job to avoid issues

So you can enable the actions themselves, but disable "Can open actions menu"
{% endhint %}

### Check identity

```lua
-- Trigger to start check identity action
TriggerEvent("jobs_creator:actions:checkIdentity")
```

## Check vehicle owner

```lua
-- Trigger to start check vehicle owner action
TriggerEvent("jobs_creator:actions:checkVehicleOwner")
```

## Create billing

```lua
-- Trigger to start billing action
TriggerEvent("jobs_creator:actions:createBilling")
```

## Drag player

```lua
-- Trigger to start drag action
TriggerEvent("jobs_creator:actions:drag")
```

## Handcuff player

```lua
-- Trigger to start soft handcuff action
TriggerEvent("jobs_creator:actions:softHandcuff")

-- Trigger to start hard handcuff action
TriggerEvent("jobs_creator:actions:hardHandcuff")
```

## Heal big

```lua
-- Trigger to start heal big action
TriggerEvent("jobs_creator:actions:healBig")
```

## Heal small

```lua
-- Trigger to start heal small action
TriggerEvent("jobs_creator:actions:healSmall")
```

## Impound

```lua
-- Trigger to start impound action
TriggerEvent("jobs_creator:actions:impoundVehicle")
```

## Licenses menu

```lua
-- Trigger to view licenses menu action
TriggerEvent("jobs_creator:actions:checkLicenses")
```

## Lockpick car

```lua
-- Trigger to start lockpick car action
TriggerEvent("jobs_creator:actions:lockpickCar")
```

## Put in car

```lua
-- Trigger to start put in car action
TriggerEvent("jobs_creator:actions:putInCar")
```

## Take from car

```lua
-- Trigger to start take from car action
TriggerEvent("jobs_creator:actions:takeFromCar")
```

## Repair vehicle

```lua
-- Trigger to start repair vehicle action
TriggerEvent("jobs_creator:actions:repairVehicle")
```

## Revive

```lua
-- Trigger to start revive action
TriggerEvent("jobs_creator:actions:revive")
```

## Search

```lua
-- Trigger to start search action
TriggerEvent("jobs_creator:actions:search")
```

## Wash vehicle

```lua
-- Trigger to start wash vehicle action

TriggerEvent("jobs_creator:actions:washVehicle")
```

## Open placeable objects menu

```lua
-- Trigger to open placeable objects menu
TriggerEvent("jobs_creator:actions:placeObject")
```