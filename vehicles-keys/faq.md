# FAQ

This page has FAQs related **ONLY to this script**, be sure to also check [common-faq.md](../jaksams-scripts/common-faq.md "mention") for other issues

<details>

<summary>Hitch warning / Performance</summary>

If your server is showing hitches/performance issues, it's because in `vehicles_keys/integrations/sv_integrations.lua` you have the option `CONTINUOUSLY_REFRESH_PLAYERS_OWNED_VEHICLES` enabled

If you will disable the option, it won't cause performance issues, but you'll have to use the exports from the documentation to refresh the players owned vehicle (for example after they buy a new vehicle from a shop)

You can refer to [this page](fix-hotwiring-bought-car.md) to find some premade **examples**

_Note: external scripts integration is completely down to you_

</details>

<details>

<summary>Cannot enter vehicle</summary>

If after destroying a vehicle window, you can't enter the vehicle, it means you still have the script `qb-vehicleskeys` started.

Remove it to solve the issue

</details>
