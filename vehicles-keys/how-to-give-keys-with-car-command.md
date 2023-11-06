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

### Newer ESX

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

### ESX 1.10

```lua
-- es_extended/server/commands.lua
ESX.RegisterCommand('car', 'admin', function(xPlayer, args, showError)
	if not xPlayer then
		return showError('[^1ERROR^7] The xPlayer value is nil')
	end

	local playerPed = GetPlayerPed(xPlayer.source)
	local playerCoords = GetEntityCoords(playerPed)
	local playerHeading = GetEntityHeading(playerPed)
	local playerVehicle = GetVehiclePedIsIn(playerPed)

	if not args.car or type(args.car) ~= 'string' then
		args.car = 'adder'
	end

	if playerVehicle then
		DeleteEntity(playerVehicle)
	end

	if Config.AdminLogging then
		ESX.DiscordLogFields("UserActions", "Spawn Car /car Triggered!", "pink", {
			{ name = "Player",  value = xPlayer and xPlayer.name or "Server Console",   inline = true },
			{ name = "ID",      value = xPlayer and xPlayer.source or "Unknown ID", inline = true },
			{ name = "Vehicle", value = args.car,       inline = true }
		})
	end

	ESX.OneSync.SpawnVehicle(args.car, playerCoords, playerHeading, upgrades, function(networkId)
		if networkId then
			local vehicle = NetworkGetEntityFromNetworkId(networkId)
			for _ = 1, 20 do
				Wait(0)
				SetPedIntoVehicle(playerPed, vehicle, -1)

				if GetVehiclePedIsIn(playerPed, false) == vehicle then
					break
				end
			end
			
			-- jaksam's vehicles keys integration
			SetTimeout(2000, function() 
			  exports["vehicles_keys"]:giveVehicleKeysToPlayerId(xPlayer.source, GetVehicleNumberPlateText(vehicle), "temporary")
			end)
			
			if GetVehiclePedIsIn(playerPed, false) ~= vehicle then
				showError('[^1ERROR^7] The player could not be seated in the vehicle')
			end
		end
	end)
end, false, {
	help = TranslateCap('command_car'),
	validate = false,
	arguments = {
		{ name = 'car', validate = false, help = TranslateCap('command_car_car'), type = 'string' }
	}
})
```

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
