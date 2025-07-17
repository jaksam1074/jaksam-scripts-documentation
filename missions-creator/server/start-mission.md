# Start a mission
Export to manually start a mission server side, in case you want to integrate it with your code

## Export: startMission
```lua
exports["missions_creator"]:startMission(templateId, playerIdOrArray)
```

#### Parameters
| Name               | Data Type | Description                |
| ------------------ | --------- | -------------------------- |
| `templateId`         | integer   | The mission template ID              |
| `playerIdOrArray` | integer|table    | Player server ID or an array of player server IDs|

#### Return value

| Name           | Data Type | Description                   |
| -------------- | --------- | ----------------------------- |
| `instanceId` | number   | The instance ID of the newly created mission or nil if the mission could not be created |