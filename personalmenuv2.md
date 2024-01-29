

# Personal Menu v2
**You can search for icons on this website <a href="https://fontawesome.com/v5/search?s=solid%2Cbrands">Link</a>**<br>
**Pre configured config for ESX**
```lua
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
```
**Pre configured config for QBCore**
```lua
LoadFrameWork = function()
    local QBCore = exports['qb-core']:GetCoreObject()
    return QBCore
end

PlayerJob = function()
    local QBCore = exports['qb-core']:GetCoreObject()
    return QBCore.Functions.GetPlayerData().job.name
end
```

**Pre configured config for Standalone**
```lua
LoadFrameWork = function()
    return {}
end

PlayerJob = function()
    return 'none'
end
```

**Work Menu**
```lua
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
```
**Commands**
```lua
{
    shouldclose = false or true,
    label = "Label here",
    submenu = false,
    event = "AXFW:PersonalMenu:Command",
    parameter = "Command Here",
    icon = "icon here"
}
```
