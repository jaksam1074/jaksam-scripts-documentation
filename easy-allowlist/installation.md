# Installation

The installation of the script is extremely easy

{% hint style="danger" %}
Do NOT use **FileZilla** to upload the files, otherwise the script will NOT work

Use [WinSCP](https://winscp.net/eng/download.php) instead
{% endhint %}

## Steps

1. Download the script and extract it in your resources
2. Add the script in your auto start (example: server.cfg)
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `easy_allowlist/sql/` folder
4. To add yourself to whitelist, you can use `add_allowlist REQUEST_ID` command in server console after you have sent the request
5. Setup the in-game settings by also following this guide

You are ready to go! Enjoy the script 😁

## Optional

After the database is setup correctly, you can delete the files in `easy_allowlist/sql/` folder, so the script won't try to setup the database each time you start the script
