**Pre configured config for ESX**
````
LoadFrameWork = function()
    TriggerEvent('esx:getSharedObject', function(obj) ESX = obj end)
    Wait(500)
    return ESX
end

PlayerJob = function()
    return ESX.GetPlayerData().job.name
end
````
**Pre configured config for QBCore**
````
LoadFrameWork = function()
    local QBCore = exports['qb-core']:GetCoreObject()
    return QBCore
end

PlayerJob = function()
    return QBCore.Functions.GetPlayerData().job.name
end
````

**Work Menu**
````
 ['jobname'] = {
    {
       shouldclose = true or false,
       label = "Label",
       submenu = false or {submenu config},
       type = "client or server",
       event = "eventname",
       parameter = "parameter or remove this convar",
       icon = "icon class"
    },
 }
 ````
