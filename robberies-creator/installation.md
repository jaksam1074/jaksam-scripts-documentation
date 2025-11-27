# Installation

## Installation

The installation of the script is extremely easy

{% hint style="danger" %}
Do NOT use **FileZilla** to upload the files, otherwise the script will NOT work

Use [WinSCP](https://winscp.net/eng/download.php) instead
{% endhint %}

{% tabs %}
{% tab title="ESX" %}
1. Download the script and extract it in your resources
2. Add the script in your auto start (example: server.cfg)
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `robberies_creator/sql/` folder
4. Download and start the [cracking safe script](https://github.com/VHall1/pd-safe) _(Credits to_ [_VHall1_](https://github.com/VHall1)_)_
5. Download and start the [lockpicking script](https://github.com/baguscodestudio/lockpick) _(Credits to_ [_baguscodestudio_](https://github.com/baguscodestudio/lockpick)_)_
6. Optional - Download and start the [datacrack minigame script ](https://github.com/utkuali/datacrack)_(Credits to_ [_utkuali_](https://github.com/utkuali)_)_
7. Optional - Download and start the [fingerprint minigame script ](https://github.com/utkuali/Finger-Print-Hacking-Game)_(Credits to_ [_utkuali_](https://github.com/utkuali)_)_
8. Optional - Download and start the [memory minigame script](https://github.com/ultrahacx/ultra-keypackhack) _(Credits to_ [_ultrahacx_](https://github.com/ultrahacx)_)_

### Adding the items - Optional <a href="#adding-the-items-optional" id="adding-the-items-optional"></a>

To add the premade items, you only have to run the file `robberies_creator/sql/items_limit.sql` **or** `robberies_creator/sql/items_weight.sql` depending on your server, if it uses the limit or the weight

{% hint style="info" %}
The latest version of ESX uses **weight**
{% endhint %}

{% hint style="danger" %}
If it doesn't work, be sure to use the latest version of the official ESX with the dependencies
{% endhint %}
{% endtab %}

{% tab title="QBCore" %}
1. Download the script and extract it in your resources
2. Add the script in your auto start (example: server.cfg)
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `robberies_creator/sql/` folder
4. Download and start the [cracking safe script](https://github.com/VHall1/pd-safe) _(Credits to_ [_VHall1_](https://github.com/VHall1)_)_
5. Download and start the [lockpicking script](https://github.com/baguscodestudio/lockpick) _(Credits to_ [_baguscodestudio_](https://github.com/baguscodestudio/lockpick)_)_
6. Optional - Download and start the [datacrack minigame script ](https://github.com/utkuali/datacrack)_(Credits to_ [_utkuali_](https://github.com/utkuali)_)_
7. Optional - Download and start the [fingerprint minigame script ](https://github.com/utkuali/Finger-Print-Hacking-Game)_(Credits to_ [_utkuali_](https://github.com/utkuali)_)_
8. Optional - Download and start the [memory minigame script](https://github.com/ultrahacx/ultra-keypackhack) _(Credits to_ [_ultrahacx_](https://github.com/ultrahacx)_)_

### Adding the items - Optional <a href="#adding-the-items-optional-1" id="adding-the-items-optional-1"></a>

To add the new items, you have to edit `qb-core/shared/items.lua` file and add at the bottom of the table the following code

```
-- Robberies Creator items
	['hacking_computer'] 			 = {['name'] = 'hacking_computer', 				['label'] = 'Hacking computer',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png', 		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Computer to hack panels'},
	['thermal_charge'] 			 = {['name'] = 'thermal_charge', 				['label'] = 'Thermal charge',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png', 		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Use to melt some doors'},
	['gas_mask'] 			 = {['name'] = 'gas_mask', 				['label'] = 'Gas mask',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png', 		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Protects from lethal gas'},
	['drill'] 			 = {['name'] = 'drill', 				['label'] = 'Drill',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png', 		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Can be used to open trucks doors'},
	['gold_ingot'] 			 = {['name'] = 'gold_ingot', 				['label'] = 'Gold ingot',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png', 		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Goooold'},
	['diamonds_box'] 			 = {['name'] = 'diamonds_box', 				['label'] = 'Diamond box',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png', 		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Diamooonds'},
	['lockpick'] 			 = {['name'] = 'lockpick', 				['label'] = 'Lockpick',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png', 		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Used to lockpick doors'},
	['painting'] 			 = {['name'] = 'painting', 				['label'] = 'Painting',	['weight'] = 500, 		['type'] = 'item', 		['image'] = 'your_image.png', 		['unique'] = false,		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Expensive painting'},
```



**Screenshot example**



<figure><img src="https://documentation.jaksam-scripts.com/~gitbook/image?url=https%3A%2F%2F3735039044-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FFH9TH8An8XLjMiOMvVGb%252Fuploads%252FcH2L891VYB7fs7ifKuHQ%252Fqb_core_robberies_creator_items.png%3Falt%3Dmedia%26token%3Dbf328cbd-a8e2-406c-87f4-daba6c1206f5&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=b9c4df58dc60a3caaeebb11757d163c2feb79775bef294314bb213b43e1e5e87" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% tab title="OX Inventory" %}
Here's a list for items to use with OX inventory, you can even use it with jaksam's inventory, in 'import from code' setting
```lua
['hacking_computer'] = {
    label = 'Hacking computer',
    weight = 500,
    stack = true,
    close = true,
    description = 'Computer to hack panels'
},

['thermal_charge'] = {
    label = 'Thermal charge',
    weight = 500,
    stack = true,
    close = true,
    description = 'Use to melt some doors'
},

['gas_mask'] = {
    label = 'Gas mask',
    weight = 500,
    stack = true,
    close = true,
    description = 'Protects from lethal gas'
},

['drill'] = {
    label = 'Drill',
    weight = 500,
    stack = true,
    close = true,
    description = 'Can be used to open trucks doors'
},

['gold_ingot'] = {
    label = 'Gold ingot',
    weight = 500,
    stack = true,
    close = true,
    description = 'Goooold'
},

['diamonds_box'] = {
    label = 'Diamond box',
    weight = 500,
    stack = true,
    close = true,
    description = 'Diamooonds'
},

['lockpick'] = {
    label = 'Lockpick',
    weight = 500,
    stack = true,
    close = true,
    description = 'Used to lockpick doors'
},

['painting'] = {
    label = 'Painting',
    weight = 500,
    stack = true,
    close = true,
    description = 'Expensive painting'
},
```
{% endtab %}
{% endtabs %}

You are ready to go! Enjoy the script 😁

## Optional step

After the database is setup correctly, you can delete the files in `robberies_creator/sql/` folder, so the script won't try to setup the database each time you start the script
