# Mission failed
Event triggered on mission fail

## Event
Add this event in any server file you want to use it in
```lua
RegisterNetEvent("missions_creator:missionFailed", function(instanceId, missionId, players, reason)

end)
```

### Parameters

| Name      | Data Type | Description                                    |
| --------- | --------- | ---------------------------------------------- |
| `instanceId`  | integer   | Unique session ID |
| `missionId` | integer    | Mission ID, the one you see in admin menu |
| `players` | table    | Table containing players who partecipate the mission |
| `reason` | string    | The reason the mission has failed |