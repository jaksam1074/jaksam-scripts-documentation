# Do I have to manually add code?
Usually you are not required to add any code. Despite this, different scripts start order may cause other scripts to not recognize Jobs Creator jobs on QBCore

# How can I fix this?
The solution is very easy, you can add the following event client side and server side in the script that is not recognizing the Jobs Creator jobs

```lua
-- jaksam's Jobs Creator integration
AddEventHandler('jobs_creator:injectJobs', function(jobs)
    -- Assign the new jobs to the QBCore object, the following line depends on how your script is structured
    QBCore.Shared.Jobs = jobs 
end)
```