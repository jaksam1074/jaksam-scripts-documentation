# Mission started
Event triggered on mission start

## Event
Add this event in any server file you want to use it in
```lua
RegisterNetEvent("missions_creator:missionStarted", function(instanceId, missionId, players)

end)
```

### Parameters

| Name      | Data Type | Description                                    |
| --------- | --------- | ---------------------------------------------- |
| `instanceId`  | integer   | Unique session ID |
| `missionId` | integer    | Mission ID, the one you see in admin menu |
| `players` | table    | Table containing players who partecipate the mission |