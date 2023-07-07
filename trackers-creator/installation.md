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
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `trackers_creator/sql/` folder

## Adding the items - Optional

To add the premade items, you only have to run the file `trackers_creator/sql/items_limit.sql` **or** `trackers_creator/sql/items_weight.sql` depending on your server, if it uses the limit or the weight

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
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `trackers_creator/sql/` folder

## Adding the items - Optional

To add the new items, you have to edit `qb-core/shared/items.lua` file and add at the bottom of the table the following code

```
	['tracker_sender'] = {['name'] = 'tracker_sender', ['label'] = 'Tracker sender', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = false, ['shouldClose'] = false, ['combinable'] = nil},
	['tracker_receiver'] = {['name'] = 'tracker_receiver', ['label'] = 'Tracker receiver', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = false, ['shouldClose'] = false, ['combinable'] = nil},
	['private_tracker'] = {['name'] = 'private_tracker', ['label'] = 'Private tracker', ['weight'] = 500, ['type'] = 'item', ['image'] = 'your_image.png', ['unique'] = false, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil},
```
{% endtab %}
{% endtabs %}

You are ready to go! Enjoy the script 😁

## Optional step

After the database is setup correctly, you can delete the files in `trackers_creator/sql/` folder, so the script won't try to setup the database each time you start the script

