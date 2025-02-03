# Installation

The installation of the script is extremely easy

{% hint style="danger" %}
Do NOT use **FileZilla** to upload the files, otherwise the script will NOT work

Use [WinSCP](https://winscp.net/eng/download.php) instead
{% endhint %}

## Steps

1. Download the script and extract it in your resources
2. Add the script in your auto start (example: server.cfg)
3. The script will **automatically** setup the database, in case it doesn't, you can manually run the files in `dealerships_creator/sql/` folder

You are ready to go! Enjoy the script 😁

## Optional step

After the database is setup correctly, you can delete the files in `dealerships_creator/sql/` folder, so the script won't try to setup the database each time you start the script

## Automatic images creation - Optional
If you want to use the automatic images creation, follow these steps:
1. Install [screenshot-basic](https://github.com/citizenfx/screenshot-basic) (you probably already have it)
2. Install [yarn](https://github.com/citizenfx/cfx-server-data) (you probably already have it -> `resources/[system]/[builders]`)
3. Install [webpack](https://github.com/citizenfx/cfx-server-data) (you probably already have it -> `resources/[system]/[builders]`)
4. Make sure `dealerships_creator` folder and `dealerships_creator/_vehicles_images` folder have the write/read permissions (right click on the folders -> properties -> enable read (**R**) and write (**W**) permissions)