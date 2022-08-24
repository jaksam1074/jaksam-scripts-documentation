# Switch vehicle lock

Triggering this event (from client side) will switch the lock of the vehicle with that plate, so it will remove all keys to other players that the vehicle owner has previously shared

### Event

```lua
TriggerServerEvent("vehicles_keys:switchLock", plate)
```

### Parameters

| Name    | Data Type | Description              |
| ------- | --------- | ------------------------ |
| `plate` | string    | The plate of the vehicle |
