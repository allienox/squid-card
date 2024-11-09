This squid card item you can use.

 exports.ox_inventory:closeInventory() you can change this at line 18.

for ox_inventory :

["squid-card"] = {
		label = "squidcard",
		weight = 1,
		stack = true,
		close = false,
		description = "squid card.",
		client = {
			image = "squid-Game.png",
		}
	},
    
    for qb-invetory : shared/item.lua

    ["squid-card"] 	 = {["name"] = "squid-card",	["label"] = "squidcard", 	["weight"] = 1, 	["type"] = "item", 	 ["image"] = "squid-Game.png", 		["unique"] = false, 	["useable"] = true, 	["shouldClose"] = true,    ["combinable"] = nil,   ["description"] = "squid card"},


if you want to change number of card you can add this on cl_main.lua line '2'.


 RegisterCommand('squid-number', function(s,a,r)
    local newNum = a[1]
    if newNum then 
        local len = string.len(newNum)
        if len <= 10 and len > 0 then
            SendNUIMessage({
                action = "newnumber",
                number = newNum,

            })
        else
            exports["origen-notify"]:SendAlert('error', 'The number must be between 1 - 10 numbers.')
        end
    else
        exports["origen-notify"]:SendAlert('error', 'You must enter a new number for the card.')
    end
end)
 

    This for add command like /squid-card and the card well be showen.

RegisterCommand('squid-card', function(s,a,r)
    if not opened then
        SendNUIMessage({
            action = "show"
        })
        SetNuiFocus(true, true)
    else
        SendNUIMessage({
            action = "close"
        })
        SetNuiFocus(false, false)
    end
end) 