# Installation

The installation of the script is extremely easy

{% hint style="danger" %}
Do NOT use **FileZilla** to upload the files, otherwise the script will NOT work

Use [WinSCP](https://winscp.net/eng/download.php) instead
{% endhint %}

{% tabs %}
{% tab title="ESX" %}
1. Download the script and extract it in your resources
2. Add the script in your auto start (example: server.cfg)
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `drugs_creator/sql/` folder

## Adding the items - Optional

If you want to use the default items/drugs, follow the steps below

To add the premade items/drugs, you only have to run the file `drugs_creator/sql/items_limit.sql` **or** `drugs_creator/sql/items_weight.sql` depending on your server, if it uses the limit or the weight

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
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `drugs_creator/sql/` folder

## Adding the items - Optional

To add the new items, you have to edit `qb-core/shared/items.lua` file and add at the bottom of the table the following code

```lua
	['ammonium_nitrate'] = {['name'] = 'ammonium_nitrate', ['label'] = 'Ammonium nitrate', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['carbon'] = {['name'] = 'carbon', ['label'] = 'Carbon', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['codeine'] = {['name'] = 'codeine', ['label'] = 'Codeine', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['drink_sprite'] = {['name'] = 'drink_sprite', ['label'] = 'Sprite', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['drug_ecstasy'] = {['name'] = 'drug_ecstasy', ['label'] = 'Ecstasy', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['drug_lean'] = {['name'] = 'drug_lean', ['label'] = 'Lean', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['drug_lsd'] = {['name'] = 'drug_lsd', ['label'] = 'LSD', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['drug_meth'] = {['name'] = 'drug_meth', ['label'] = 'Meth', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['hydrogen'] = {['name'] = 'hydrogen', ['label'] = 'Hydrogen', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['ice'] = {['name'] = 'ice', ['label'] = 'Ice', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['jolly_ranchers'] = {['name'] = 'jolly_ranchers', ['label'] = 'Jolly Ranchers', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['liquid_sulfur'] = {['name'] = 'liquid_sulfur', ['label'] = 'Liquid Sulfur', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['muriatic_acid'] = {['name'] = 'muriatic_acid', ['label'] = 'Muriatic Acid', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['nitrogen'] = {['name'] = 'nitrogen', ['label'] = 'Nitrogen', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['oxygen'] = {['name'] = 'oxygen', ['label'] = 'Oxygen', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['pseudoefedrine'] = {['name'] = 'pseudoefedrine', ['label'] = 'Pseudoefedrine', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['red_sulfur'] = {['name'] = 'red_sulfur', ['label'] = 'Red Sulfur', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['sodium_hydroxide'] = {['name'] = 'sodium_hydroxide', ['label'] = 'Sodium hydroxide', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['water'] = {['name'] = 'water', ['label'] = 'Water', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['cannabis'] = {['name'] = 'cannabis', ['label'] = 'Cannabis', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['green_gelato_cannabis'] = {['name'] = 'green_gelato_cannabis', ['label'] = 'Green Gelato Cannabis', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['opium'] = {['name'] = 'opium', ['label'] = 'Opium', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
	['cocaine'] = {['name'] = 'cocaine', ['label'] = 'Cocaine', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = false, ['combinable'] = nil},
```

**Screenshot example**

<figure><img src="../.gitbook/assets/qb_core_drugs_creator_items.jpg" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

You are ready to go! Enjoy the script 😁

## Optional step

After the database is setup correctly, you can delete the files in `drugs_creator/sql/` folder, so the script won't try to setup the database each time you start the script

