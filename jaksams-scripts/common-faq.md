# Common FAQ

This page contains common FAQ shared for all scripts, if your issue is not in this page, be sure to check the FAQ of the script you are having issues with

<details>

<summary>Crash</summary>

Crashes can be caused by 2 things:

* You have to whitelist these objects models in your anticheat:`L1_1`• `GetHashKey('L1_1')`• `2116969379`

<!---->

* If you still experience crashes after whitelisting those objects models in your anticheat, you can refer to [this page](fix-server-crash-on-script-start.md)

_If you don't know how to whitelist objects models in your anticheat, ask to your anticheat creator_

</details>

<details>

<summary>Attempted to index a nil value (field 'ESX')</summary>

If you have this error, it means the script couldn't retrieve the shared object of ESX.

This error might be caused by other errors you have in your server/F8 console, which happens before it does.

If you don't have any other error before that one, you can refer to [this page](manually-set-esx-shared-object.md)

</details>

<details>

<summary>How to fix "missing menu_default" error</summary>

To fix the error, simply read the installation tutorial of the script

</details>

<details>

<summary>Objects/Props not spawning</summary>

If the props don't spawn, it's very probably an issue with your anticheat

Be sure to whitelist all the props in your anticheat, if you don't know how, ask to your anticheat creator

</details>

<details>

<summary>Can't receive ANY item</summary>

If you have already tried with different items and you can't receive any of them, check [this page](issues-with-items.md)

</details>

<details>

<summary>Can't receive WEAPONS ONLY</summary>

If only weapons cause issues but items work fine, these are the possible reasons:

* On ESX, it's most likely because your server doesn't support the standard ESX method `xPlayer.addWeapon`

<!---->

* On QBCore, it may be that your inventory is changing the default behaviour of qb-inventory

This is not an issue which depends on the script, but on your framework/inventory and cannot be solved by us, the standard methods must work

</details>

<details>

<summary>How to replace default notifications</summary>

To replace the notifications of any script, you can refer to the documentation of the script, it has events that allows you to disable the default one and call an external one

_Note: external scripts integration is completely down to you_

</details>

<details>

<summary>How to replace the default progress bar</summary>

To replace the progress bar of any script, you can refer to the documentation of the script, it has events that allows you to disable the default one and call an external one

_Note: external scripts integration is completely down to you_

</details>

<details>

<summary>Scripts transferes</summary>

Scripts can be transferred one time only through the FiveM keymaster, by using the side button instead of “Download”. There are no manual revoke or manual transfers in any situation at all

</details>

<details>

<summary>Refunds</summary>

Purchases in jaksam’s store are final, this applies for any situation, wrong framework, wrong accounts, etc. So in case of refunds, unfortunately we cannot help with them at all

</details>
