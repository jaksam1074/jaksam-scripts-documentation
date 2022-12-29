# Self give vehicle plate

You can use this event to self give a vehicle plate, for example in the events where your framework spawns a vehicle with /car command

## Event

```lua
TriggerServerEvent("vehicles_keys:selfGiveVehicleKeys", plate)
```

## Example

```lua
-- For ESX, in es_extended/client/main.lua
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

-- For QBCore, in qb-core/client/events.lua
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
