# How to add minigames
Adding new minigames is easy. Follow the procedure to add a new minigame:
1. Duplicate the file `missions_creator/client/minigames/_EXAMPLE_MINIGAME.lua`
2. Rename the file to your minigame name
3. Open the new file, remove the comments at the beginning and at the end of the file (so remove these symbols: `--[[` and `--]]`)
4. Change `YOUR_MINIGAME_NAME` to your minigame name
5. Edit the function to support your minigame, it must return true on success and false on failure. You can see the examples with `datacrack.lua`, `fingerprint.lua` and `memory_game.lua`
6. Save the file and restart the script. If you did everything correctly (especially implementing the minigame itself), you should see your minigame in the list of minigames in the script