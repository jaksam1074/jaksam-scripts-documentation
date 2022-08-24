# Home

Here you will find all documentations of jaksam's scripts, some pages may require coding knowledge

## How to use the documentations

Most of the scripts will have a folder named **integrations**, where you can add the integration code at the bottom of the files. So most of the times, you will only need to add your code inside these files, not in other scripts

Be sure to read carefully the comments, they will explain you everything you need above the lines of code

Integrations files:

* `integrations/cl_integrations.lua` - Here there will be the code for **client side** scripts, as for example replacing the notifications or progress bar (usually here you can insert the code from `Client` category of the documentations)
* `integrations/sh_integrations.lua` - Here there will be the code that will run **both on client side and server side**, usually there will be the external scripts names, so you will be able to edit the names if your server uses a different name than the default one
* `integrations/sv_integrations.lua` - Here there will be the code for **server side** scripts (usually here you can insert the code from `Server` category of the documentations)

If you are looking for an option that you can't find in normal config/settings, probably it will be inside the integrations files
