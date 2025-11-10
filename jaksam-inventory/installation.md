# Installation

## Installation

The installation of the script is extremely easy

{% hint style="danger" %}
Do NOT use **FileZilla** to upload the files, otherwise the script will NOT work

Use [WinSCP](https://winscp.net/eng/download.php) instead
{% endhint %}

{% tabs %}

{% tab title="ESX 1.10.7" %}
1. Download the script and extract it in your resources
2. Download the jaksam_core and extract it in your resources
3. Add the script in your auto start, **right after** `es_extended` (example: server.cfg)
4. Set in `es_extended\config.lua` -> `Config.OxInventory = false`
5. Set in `es_extended\config.lua` -> `Config.EnableDefaultInventory = false`
6. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `jaksam_inventory/sql/` folder

Start order example
```
# OX
ensure oxmysql
ensure ox_lib

## ESX
ensure es_extended
ensure jaksam_inventory

# Other ESX scripts (start instead of ensure, otherwise es_extended would restart if it's in this folder)
start [core]
```

{% hint style="warning" %}
If it doesn't work, be sure to use the latest version of the official ESX with the dependencies
{% endhint %}
{% endtab %}

{% tab title="ESX 1.11.3+" %}
1. Download the script and extract it in your resources
2. Download the jaksam_core and extract it in your resources
3. Add the script in your auto start, **right after** `es_extended` (example: server.cfg)
4. Set in `es_extended\config.lua` -> `Config.CustomInventory = "jaksam_inventory"`
5. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `jaksam_inventory/sql/` folder

Start order example
```
# OX
ensure oxmysql
ensure ox_lib

## ESX
ensure es_extended
ensure jaksam_inventory

# Other ESX scripts (start instead of ensure, otherwise es_extended would restart if it's in this folder)
start [core]
```

{% endtab %}

{% tab title="QBCore" %}
1. Download the script and extract it in your resources
2. Download the jaksam_core and extract it in your resources
3. Enable `Integrations.backwardsCompatibility` for qb-inventory in `jaksam_inventory\integrations\sv_integrations.lua`
4. Add `jaksam_inventory` in your auto start, **right after** `qb-core` (example: server.cfg)
5. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `jaksam_inventory/sql/` folder

Start order example
```
# OX
ensure oxmysql
ensure ox_lib

## QBCore
ensure qb-core
ensure jaksam_inventory
# Other QBCore scripts
```

{% hint style="warning" %}
If it doesn't work, be sure to use the latest version of the official QBCore with the dependencies
{% endhint %}
{% endtab %}


{% tab title="QBX" %}
1. Download the script and extract it in your resources
2. Download the jaksam_core and extract it in your resources
3. Enable `Integrations.backwardsCompatibility` for ox_inventory in `jaksam_inventory\integrations\sv_integrations.lua`
4. Add `jaksam_inventory` in your auto start, **right after** `qbx_core` (example: server.cfg)
5. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `jaksam_inventory/sql/` folder

Start order example
```
# OX
ensure oxmysql
ensure ox_lib

## QBX
ensure qbx_core
ensure jaksam_inventory
# Other QBX scripts
```

{% hint style="warning" %}
If it doesn't work, be sure to use the latest version of the official QBX with the dependencies
{% endhint %}
{% endtab %}

{% endtabs %}

You are ready to go! Enjoy the script 😁

## Importing old items and inventories
{% tabs %}

{% tab title="ESX" %}
1. Go in-game
2. Use /inventory command, go in settings
3. Click button "Import from ESX"
4. Done!
{% endtab %}

{% tab title="QBCore" %}
1. Only during this process, make sure the **original qb-inventory** is running (then you can and should remove it)
2. Use /inventory command, go in settings
3. Click button "Import from QBCore"
4. Done!
{% endtab %}

{% tab title="OX inventory" %}
1. Only during this process, make sure the ox_inventory is running (then you can and should remove it)
2. Use /inventory command, go in settings
3. Click button "Import from OX inventory"
4. Done!
{% endtab %}

{% tab title="qs-inventory" %}
1. Only during this process, make sure the qs_inventory is running (then you can and should remove it)
2. Use /inventory command, go in settings
3. Click button "Import from qs-inventory"
4. Done!
{% endtab %}

{% tab title="Chezza inventory" %}
1. Only during this process, make sure the Chezza inventory is running (then you can and should remove it)
2. Use /inventory command, go in settings
3. Click button "Import from Chezza inventory"
4. Done!
{% endtab %}

{% tab title="TGiann inventory" %}
1. Only during this process, make sure the TGiann inventory is running (then you can and should remove it)
2. Use /inventory command, go in settings
3. Click button "Import from TGiann inventory"
4. Done!
{% endtab %}

{% endtabs %}

## Backwards Compatibility
This inventory lets you use your old scripts, even if they need another inventory

### Default Framework Functions
You can use the normal inventory functions from your framework

### 'OX Inventory' Compatibility
If your old scripts use 'OX Inventory', you can enable easy compatibility

1. Go in `jaksam_inventory\integrations\sv_integrations.lua`
2. Enable `ox_inventory` in `Integrations.backwardsCompatibility`
3. Server may require a restart after it loads the first time with these settings

### 'QB Inventory' Compatibility
If your old scripts use 'QB Inventory', you can enable easy compatibility

1. Go in `jaksam_inventory\integrations\sv_integrations.lua`
2. Enable `qb-inventory` in `Integrations.backwardsCompatibility`
3. Server may require a restart after it loads the first time with these settings

That's all, your old scripts should work with this inventory