# Installation

The installation of the script is extremely easy

## Steps

1. Download the script and extract it in your resources
2. Add the script in your auto start (example: server.cfg)
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `vehicles_keys/sql/` folder
4. (QBCore only) Download and extract [this script](https://cdn.discordapp.com/attachments/895599870268817418/987388095169179688/menu\_default.rar) in your resources, **without renaming it**

You are ready to go! Enjoy the script 😁

## Optional step

After the database is setup correctly, you can delete the files in `vehicles_keys/sql/` folder, so the script won't try to setup the database each time you start the script

## Adding the items - Optional

### ESX

To add the premade items, you only have to run the file `vehicles_keys/sql/items_limit.sql` **or** `vehicles_keys/sql/items_weight.sql` depending on your server, if it uses the limit or the weight

### QBCore

To add the new items, you have to edit `qb-core/shared/items.lua` file and add at the bottom of the table the following code

```lua
	-- Vehicles Keys items
	['vehicle_alarm_1'] 			 = {['name'] = 'vehicle_alarm_1', 				['label'] = 'Vehicle alarm level 1',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png',		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Vehicle alarm level 1'},
	['vehicle_alarm_2'] 			 = {['name'] = 'vehicle_alarm_2', 				['label'] = 'Vehicle alarm level 2',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png', 		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Vehicle alarm level 2'},
	['vehicle_alarm_3'] 			 = {['name'] = 'vehicle_alarm_3', 				['label'] = 'Vehicle alarm level 3',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png', 		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Vehicle alarm level 3'},
	['vehicle_alarm_4'] 			 = {['name'] = 'vehicle_alarm_4', 				['label'] = 'Vehicle alarm level 4',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png', 		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Vehicle alarm level 4'},
```

#### Screenshot example

<figure><img src="../.gitbook/assets/qb_core_vehicles_keys_items.png" alt=""><figcaption></figcaption></figure>
