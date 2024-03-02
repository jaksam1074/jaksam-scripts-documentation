# Installation

The installation of the script is extremely easy

{% hint style="danger" %}
Do NOT use **FileZilla** to upload the files, otherwise the script will NOT work

Use [WinSCP](https://winscp.net/eng/download.php) instead
{% endhint %}

## Steps

1. Download the script and extract it in your resources
2. Add the script in your auto start (example: server.cfg)
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `farming_creator/sql/` folder
4. (QBCore only) Download and extract the script [menu\_default (clickable link)](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing) in your resources, **without renaming it**, and add it to auto start (example: server.cfg)

You are ready to go! Enjoy the script 😁

## Optional step

After the database is setup correctly, you can delete the files in `farming_creator/sql/` folder, so the script won't try to setup the database each time you start the script
