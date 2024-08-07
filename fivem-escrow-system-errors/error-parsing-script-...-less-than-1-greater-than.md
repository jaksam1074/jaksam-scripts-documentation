# Error parsing script ... <\1>

Error message **example**:\
`Error parsing script @jobs_creator/server/markers/job_shop.lua in resource jobs_creator: @jobs_creator/server/markers/job_shop.lua:1: syntax error near '<\1>'`

## Possible reasons

* You are transferring the folder to the VPS file by file, please upload the .zip file and extract it **after** it is already on your VPS (so drag and drop the zip file and **not** the folder)
* You may have to clear the **server** caches
* The download was corrupted, try doing a new clean install
* You have a virus on your server that is modifying other script files (very likely if everything else hasn't fixed it)

## How to verify my server version?

To verify what server version your server is currently using, you have to use the following command in your FiveM server console: `version`

### Example

<figure><img src="../.gitbook/assets/version_example.jpg" alt=""><figcaption></figcaption></figure>

## How to update my server version?

To update your server version, you have to download the new [server artifacts](https://runtime.fivem.net/artifacts/fivem/build\_server\_windows/master/) and to extract and replace them in your server folder

This is the **official** [FiveM guide](https://docs.fivem.net/docs/server-manual/setting-up-a-server/) to update your server

## My server version is already updated, but I have the error

If you have the error even if your server version is not the issue, then you have to check [here](failed-to-verify-protected-resource.md)
