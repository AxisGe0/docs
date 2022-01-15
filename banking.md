**QBCore Default Configuration**
````
CreateThread(function()
    if IsDuplicityVersion() then 
        QBCore = exports['qb-core']:GetCoreObject()--Load Server Sided Framework
    else
        QBCore = exports['qb-core']:GetCoreObject()--Load Client Sided Framework
    end
end)

DrawText3Ds = function(x, y, z, text)--Client
	SetTextScale(0.35, 0.35)
    SetTextFont(4)
    SetTextProportional(1)
    SetTextColour(255, 255, 255, 215)
    SetTextEntry("STRING")
    SetTextCentre(true)
    AddTextComponentString(text)
    SetDrawOrigin(x,y,z, 0)
    DrawText(0.0, 0.0)
    local factor = (string.len(text)) / 370
    DrawRect(0.0, 0.0+0.0125, 0.017+ factor, 0.03, 0, 0, 0, 75)
    ClearDrawOrigin()
end

GetPlayerCharacterName = function()--Client
    local Player = QBCore.Functions.GetPlayerData()
    return Player.charinfo.firstname..' '..Player.charinfo.lastname
end

GetPlayerBalance = function(type)--Client
    local Player = QBCore.Functions.GetPlayerData()
    return Player.money[type]
end

WithdrawMoney = function(src,amount)--Server
    local Player = QBCore.Functions.GetPlayer(src)
    if Player.PlayerData.money.bank >= amount then
        Player.Functions.RemoveMoney('bank',amount)
        Player.Functions.RemoveMoney('cash',amount)
    end
end

DepositMoney = function(src,amount)--Server
    local Player = QBCore.Functions.GetPlayer(src)
    if Player.PlayerData.money.cash >= amount then
        Player.Functions.RemoveMoney('cash',amount)
        Player.Functions.AddMoney('bank',amount)
    end
end

TransferMoney = function(src,target,amount)--Server
    if src == target then return end
    local Player = QBCore.Functions.GetPlayer(src)
    local Target = QBCore.Functions.GetPlayer(target)
    local amount = amount and tonumber(amount)
    if Player and Target and amount and amount > 0 then 
        if Player.PlayerData.money.bank >= amount then 
            Player.Functions.RemoveMoney('bank',amount)
            Player.Functions.AddMoney('bank',amount)
        end
    end
end
````
**QBCore Default Configuration**

````
CreateThread(function()
    if IsDuplicityVersion() then 
        TriggerEvent("esx:getSharedObject",function(obj)
		    ESX = obj
	    end)--Load Server Sided Framework
    else
        TriggerEvent("esx:getSharedObject",function(obj)
            ESX = obj
        end)--Load Client Sided Framework
    end
end)

DrawText3Ds = function(x, y, z, text)--Client
	SetTextScale(0.35, 0.35)
    SetTextFont(4)
    SetTextProportional(1)
    SetTextColour(255, 255, 255, 215)
    SetTextEntry("STRING")
    SetTextCentre(true)
    AddTextComponentString(text)
    SetDrawOrigin(x,y,z, 0)
    DrawText(0.0, 0.0)
    local factor = (string.len(text)) / 370
    DrawRect(0.0, 0.0+0.0125, 0.017+ factor, 0.03, 0, 0, 0, 75)
    ClearDrawOrigin()
end

GetPlayerCharacterName = function()--Client
    return GetPlayerName(PlayerId())
end

GetPlayerBalance = function(type)--Client
    return 0---Is not ready yet should be ready in few hours
end

WithdrawMoney = function(src,amount)--Server
    local Player = ESX.GetPlayerFromId(src)
    if Player.getAccount('bank').money >= amount then
        Player.removeAccountMoney('bank', amount)
		Player.addMoney(amount)
    end
end

DepositMoney = function(src,amount)--Server
    local Player = ESX.GetPlayerFromId(src)
    if Player.getMoney() >= amount then
        Player.removeMoney(amount)
		Player.addAccountMoney('bank',amount)
    end
end

TransferMoney = function(src,target,amount)--Server
    if src == target then return end
    local Player = ESX.GetPlayerFromId(src)
    local Target = ESX.GetPlayerFromId(target)
    local amount = amount and tonumber(amount)
    if Player and Target and amount and amount > 0 then 
        if Player.getAccount('bank').money >= amount then 
            Player.removeAccountMoney('bank', amountt)
			Target.addAccountMoney('bank', amountt)
        end
    end
end
````
