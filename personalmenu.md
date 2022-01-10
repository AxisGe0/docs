**You can search for icons on this website <a href="https://fontawesome.com/v5.15/how-to-use/on-the-web/referencing-icons/basic-use">Link</a>**<br>
**Pre configured config for ESX**
````
LoadFrameWork = function()
    return {}
end

PlayerJob = function()
    local ESX = nil
    while ESX == nil do 
        TriggerEvent('esx:getSharedObject', function(obj) ESX = obj end)
        Wait(0)
    end
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
    local QBCore = exports['qb-core']:GetCoreObject()
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
**Commands**
````
{
     shouldclose = false or true,
     label = "Label here",
     submenu = false,
     event = "AXFW:PersonalMenu:Command",
     parameter = "Command Here",
     icon = "icon here"
}

