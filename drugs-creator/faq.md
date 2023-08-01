# FAQ

This page has FAQs related **ONLY to this script**, be sure to also check [common-faq.md](../jaksams-scripts/common-faq.md "mention") for other issues

<details>

<summary>Drugs effects not working</summary>

If the effects are not working, it means that `ESX.RegisterUsableItem` function of your `es_extended` doesn't work properly

You can still manually register/trigger effects by using the [following event](client/manually-start-drugs-effects.md)

On both **ESX** and **QBCore**, an anticheat may interfere with drugs effects

_Note: this is not something which depends on the script and we can't solve it for you_

</details>

<details>

<summary>Bad performance</summary>

If you are having issues with server side performance with Drugs Creator, most likely is because of NPC selling, which requires to refresh all players inventories to be able to prompt `Press E to sell drugs` dialog

You can use a [command](https://jaksam1074.gitbook.io/jaksams-scripts-documentation/drugs-creator/use-command-to-sell-to-npcs) instead of it to improve performance

</details>
