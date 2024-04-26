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
2. Download 'jaksam\_core' and extract it in your resources
3. Add 'jaksam\_core' in your auto start (example: server.cfg)
4. **After** 'jaksam\_core', start 'missions\_creator'
5. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `missions_creator/sql/` folder
6. Optional - Download and start the [datacrack minigame script ](https://github.com/utkuali/datacrack)_(Credits to_ [_utkuali_](https://github.com/utkuali)_)_
7. Optional - Download and start the  [fingerprint minigame script ](https://github.com/utkuali/Finger-Print-Hacking-Game)_(Credits to_ [_utkuali_](https://github.com/utkuali)_)_
8. Optional - Download and start the [memory minigame script](https://github.com/ultrahacx/ultra-keypackhack) _(Credits to_ [_ultrahacx_](https://github.com/ultrahacx)_)_

{% hint style="danger" %}
If it doesn't work, be sure to use the latest version of the official ESX with the dependencies
{% endhint %}
{% endtab %}

{% tab title="QBCore" %}
1. Download the script and extract it in your resources
2. Download 'jaksam\_core' and extract it in your resources
3. Add 'jaksam\_core' in your auto start (example: server.cfg)
4. **After** 'jaksam\_core', start 'missions\_creator'
5. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `missions_creator/sql/` folder
6. Optional - Download and start the [datacrack minigame script ](https://github.com/utkuali/datacrack)_(Credits to_ [_utkuali_](https://github.com/utkuali)_)_
7. Optional - Download and start the  [fingerprint minigame script ](https://github.com/utkuali/Finger-Print-Hacking-Game)_(Credits to_ [_utkuali_](https://github.com/utkuali)_)_
8. Optional - Download and start the [memory minigame script](https://github.com/ultrahacx/ultra-keypackhack) _(Credits to_ [_ultrahacx_](https://github.com/ultrahacx)_)_
{% endtab %}
{% endtabs %}

You are ready to go! Enjoy the script 😁

## Optional step

After the database is setup correctly, you can delete the files in `missions_creator/sql/` folder, so the script won't try to setup the database each time you start the script
