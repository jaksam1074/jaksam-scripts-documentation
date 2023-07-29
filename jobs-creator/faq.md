# FAQ

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

<summary>How to replace default notifications</summary>

To replace the notifications of any script, you can refer to the documentation of the script, it has events that allows you to disable the default one and call an external one

_Note: external scripts integration is completely down to you_

</details>

<details>

<summary>How to replace default progress bar</summary>

To replace the progress bar of any script, you can refer to the documentation of the script, it has events that allows you to disable the default one and call an external one

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

<summary>How to fix "missing menu_default" error</summary>

To fix the error, simply read the installation tutorial of Jobs Creator

</details>
