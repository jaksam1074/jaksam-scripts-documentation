# Failed to verify protected resource

Error message example:\
`[svadhesive] Failed to verify protected resource jobs_creator`

## Possible reasons

* You don't have `.fxap` file in the script folder
* You are using **Filezilla**
* Your server hosting is using **Filezilla** to upload the script
* You are transferring the folder to the VPS file by file, please upload the .zip file and extract it **after** it is already on your VPS (so drag and drop the zip file and **not** the folder)

## Solutions

1. Download the script again from [FiveM keymaster](https://keymaster.fivem.net/)
2. Upload the script using [WinSCP](https://winscp.net/eng/download.php) _instead of_ Filezilla
3. Restart the server
