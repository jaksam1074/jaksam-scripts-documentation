# FAQ

This page has FAQs related **ONLY to this script**, be sure to also check [common-faq.md](../jaksams-scripts/common-faq.md "mention") for other issues

<details>

<summary>How to change animations</summary>

[This is a list of usable animations](https://en.los-santos-multiplayer.com/dev.airdancer?cxt=anim)

* Bigger text is the animation dictionary
* Smaller text is animation name

[This is the list of usable scenarios](https://wiki.rage.mp/index.php?title=Scenarios)

The main difference between scenarios and animations, is that usually a scenario have a object attached to animation

_It's not possible to use external animations_

**Note: not all animations in the lists work**

</details>

<details>

<summary>How to lock jobs vehicles</summary>

To lock vehicle you have 2 possibilities:

1. You use the events and exports from the script documentation to integrate your own car lock script
2. You can use **jaksam's Vehicles Keys** which has Jobs Creator integration included

_Note: external scripts integration is completely down to you_

</details>

<details>

<summary>How does Jobs Creator handles salaries/wages?</summary>

Jobs Creator doesn't handle the salaries, this is because the framework script does it

* For ESX, `es_extended` and `esx_society` scripts handle the salaries
* For QBCore, `qb-core` handles the salaries

So you will be able to **define** the salaries in Jobs Creator, but it will be the framework giving money

</details>

<details>

<summary>How to fix "Couldn't create marker" error</summary>

This issue is caused by something wrong in `job_data` table of the database

Possible solutions:

1. Delete `job_data` table from the database and restart the script/server
2. The `id` column of the `job_data` table doesn't have **AUTO INCREMENT** as default value, you have to make it that the default value of that column is **AUTO INCREMENT**

</details>

<details>

<summary>Why outfits features don't work?</summary>

If outfits features don't work, it's because you don't have the dependencies to use them

* On ESX, you must have `esx_skin` and `skinchanger` scripts installed
* On QBCore, you must have `qb-clothing` script installed

Jobs Creator has integration for [**illenium-appearance**](https://github.com/iLLeniumStudios/illenium-appearance) that should work on both frameworks

</details>

<details>

<summary>Weapon upgrader doesn't work</summary>

In case the weapon upgrader marker doesn't work, these are 2 possible reasons:

1. You are using an addon weapon, but you didn't configure it properly in `es_extended` script
2. Your inventory edits the standard behavior of **ESX/QBCore**, so in this case you must use your own inventory instead of Jobs Creator to use weapons components and tints

</details>

<details>

<summary>Edit vehicles labels in garages</summary>

Jobs Creator retrieves the vehicles labels through FiveM natives, so to have custom labels, you'll have to configure them in your addon vehicle script.

In FiveM forums there are multiple guides on how to configure addon vehicles display names

</details>
