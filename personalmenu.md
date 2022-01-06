**Pre configuired config for ESX**
LoadFrameWork = function()
    TriggerEvent('esx:getSharedObject', function(obj) ESX = obj end)
    Wait(500)
    return ESX
end

PlayerJob = function()
    return ESX.GetPlayerData().job.name
end
