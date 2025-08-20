# Get a mission template
Export to get a mission template server side, in case you want to retrieve the data, for example options, label, description, etc.
An example of good usage, can be a custom menu that shows only a limited number of missions, and you want to show the label and description. Then you can use the export to startMission to start the mission manually

## Export: getMissionTemplate
```lua
exports["missions_creator"]:getMissionTemplate(templateId)
```

#### Parameters
| Name               | Data Type | Description                |
| ------------------ | --------- | -------------------------- |
| `templateId`         | integer   | The mission template ID              |

#### Return value

| Name           | Data Type | Description                   |
| -------------- | --------- | ----------------------------- |
| `templateData` | table   | The mission template data. See main keys below |

##### Main keys of `templateData`

| Key         | Type     | Description                                 |
| ----------- | -------- | ------------------------------------------- |
| id          | integer  | The mission template ID                     |
| label       | string   | The mission name/label                      |
| description | string   | The mission description                     |
| options     | table    | Table with mission options (see below)      |

> **Note:** The `options` table usually contains fields like `startCoordinates`, `minPlayers`, `maxPlayers`, `allowedJobs`, `canBeRepeated`, `requiredMissions`