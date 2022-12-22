# Use command to sell to NPCs

If for any reason you prefer to disable the default selling method to NPCs (the one in image below) and use a command, it's possible to do it by following this page guide

Using the command over the standard method, will improve the server performance

<figure><img src="../.gitbook/assets/immagine (1).png" alt=""><figcaption></figcaption></figure>

### How to enable the command

1. Open the file `advanced_drugs_creator/integrations/sv_integrations.lua`
2. Set to `true` the option `COMPLETELY_DISABLE_INVENTORIES_REFRESH`. This will improve the server performance, because the script will not refresh all players inventories anymore, but doing this will also make impossible to use the usual "Press E to sell drugs"
3. Choose a command for the option `COMMAND_TO_MANUALLY_SELL_TO_NPCS` to allow players using the command. Be sure to write your preferred command  between double quotes ( `" "` )

#### Final result

<figure><img src="../.gitbook/assets/immagine (1) (1).png" alt=""><figcaption></figcaption></figure>

