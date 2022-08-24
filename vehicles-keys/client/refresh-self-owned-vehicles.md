# Refresh self owned vehicles

Triggering this event (from client side) will refresh the list of the player's owned vehicles (from owned\_vehicles on ESX or player\_vehicles on QBCore)

This will be useful to update the list of owned vehicles when a player buys a new vehicle, so you can add this line of code in the code right after a successful vehicle purchase

## Event

```lua
TriggerServerEvent("vehicles_keys:refreshMineOwnedVehicles")
```
