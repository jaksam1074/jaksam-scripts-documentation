# FAQ

This page has FAQs related **ONLY to this script**, be sure to also check [common-faq.md](../jaksams-scripts/common-faq.md "mention") for other issues



<details>

<summary>How to add myself in whitelist</summary>

The script will automatically detect if the whitelist is completely empty, so you'll be automatically whitelisted the first time you join

To whitelist manually, you can send the whitelist request to your server and then use the command `add_allowlist YourRequestIdHere` in the server console

</details>

<details>

<summary>Stuck on 'deferring connection...'</summary>

If when you connect to your server, Easy Allowlist says `deferring connection...` and gets stuck without any error at all, you should try:

1. Open the file `easy_allowlist/server/deferrals.lua`
2. Search `Citizen.Wait(500)` code
3. Edit from `Citizen.Wait(500)` to `Citizen.Wait(10000)` or higher if still doesn't work
4. Save the file
5. Restart the script

</details>
