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
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `billing_ui/sql/` folder
4. Configure the options in the config files (be sure to read the comments, they'll explain you everything)

{% hint style="warning" %}
Be sure to remove esx\_billing to avoid issues
{% endhint %}
{% endtab %}

{% tab title="QBCore" %}
1. Download the script and extract it in your resources
2. Add the script in your auto start (example: server.cfg)
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `billing_ui/sql/` folder
4. Configure the options in the config files (be sure to read the comments, they'll explain you everything)
5. (QBCore only) Download and extract [the script menu\_default (clickable link)](https://cdn.discordapp.com/attachments/895599870268817418/987388095169179688/menu\_default.rar) in your resources, **without renaming it**, and add it to auto start (example: server.cfg)
{% endtab %}
{% endtabs %}

You are ready to go! Enjoy the script 😁

## Optional

After the database is setup correctly, you can delete the files in `billing_ui/sql/` folder, so the script won't try to setup the database each time you start the script
