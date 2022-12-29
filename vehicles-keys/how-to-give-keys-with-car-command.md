# How to give keys with /car command

To automatically have keys of a vehicle received with /car command, you can see the examples below

In the following examples **the integration line** has already been added to previously existing code blocks

### Old ESX

{% code title="es_extended/client/main.lua" %}
```lua
RegisterNetEvent('esx:spawnVehicle')
AddEventHandler('esx:spawnVehicle', function(vehicleName)
	local model = (type(vehicleName) == 'number' and vehicleName or GetHashKey(vehicleName))

	if IsModelInCdimage(model) then
		local playerPed = PlayerPedId()
		local playerCoords, playerHeading = GetEntityCoords(playerPed), GetEntityHeading(playerPed)

		ESX.Game.SpawnVehicle(model, playerCoords, playerHeading, function(vehicle)
			TaskWarpPedIntoVehicle(playerPed, vehicle, -1)

			-- VEHICLES KEYS INTEGRATION
			TriggerServerEvent("vehicles_keys:selfGiveVehicleKeys", GetVehicleNumberPlateText(vehicle))
		end)
	else
		TriggerEvent('chat:addMessage', {args = {'^1SYSTEM', 'Invalid vehicle model.'}})
	end
end)
```
{% endcode %}

### New ESX

{% code title="es_extended/server/commands.lua" %}
```lua
ESX.RegisterCommand('car', 'admin', function(xPlayer, args, showError)
	local GameBuild = tonumber(GetConvar("sv_enforceGameBuild", 1604))
	if not args.car then args.car = GameBuild >= 2699 and "draugur" or "prototipo" end
	ESX.DiscordLogFields("UserActions", "/car Triggered", "pink", {
		{name = "Player", value = xPlayer.name, inline = true},
		{name = "ID", value = xPlayer.source, inline = true},
    {name = "Vehicle", value = args.car, inline = true}
	})
	local upgrades = Config.MaxAdminVehicles and {
		plate = "ADMINCAR", 
		modEngine = 3,
		modBrakes = 2,
		modTransmission = 2,
		modSuspension = 3,
		modArmor = true,
		windowTint = 1,
	} or {}
	local coords = xPlayer.getCoords(true)
	local PlayerPed = GetPlayerPed(xPlayer.source)
	ESX.OneSync.SpawnVehicle(args.car, coords - vector3(0,0, 0.9), GetEntityHeading(PlayerPed), upgrades, function(networkId)
		local vehicle = NetworkGetEntityFromNetworkId(networkId)
		Wait(250)
		TaskWarpPedIntoVehicle(PlayerPed, vehicle, -1)
		
		-- VEHICLES KEYS INTEGRATION
		exports["vehicles_keys"]:giveVehicleKeysToPlayerId(xPlayer.source, GetVehicleNumberPlateText(vehicle), "temporary") 
	end)
end, false, {help = TranslateCap('command_car'), validate = false, arguments = {
	{name = 'car',validate = false, help = TranslateCap('command_car_car'), type = 'string'}
}}) 
```
{% endcode %}

### QBCore

{% code title="qb-core/client/events.lua" %}
```lua
RegisterNetEvent('QBCore:Command:SpawnVehicle', function(vehName)
    local ped = PlayerPedId()
    local hash = GetHashKey(vehName)
    local veh = GetVehiclePedIsUsing(ped)
    if not IsModelInCdimage(hash) then return end
    RequestModel(hash)
    while not HasModelLoaded(hash) do
        Wait(0)
    end
        
     if IsPedInAnyVehicle(ped) then 
        DeleteVehicle(veh)
    end
        
    local vehicle = CreateVehicle(hash, GetEntityCoords(ped), GetEntityHeading(ped), true, false)
    TaskWarpPedIntoVehicle(ped, vehicle, -1)
    SetVehicleFuelLevel(vehicle, 100.0)
    SetModelAsNoLongerNeeded(hash)
    
    -- Old event
    --TriggerEvent("vehiclekeys:client:SetOwner", QBCore.Functions.GetPlate(vehicle))

	-- VEHICLES KEYS INTEGRATION
    TriggerServerEvent("vehicles_keys:selfGiveVehicleKeys", QBCore.Functions.GetPlate(vehicle))
end)
```
{% endcode %}
