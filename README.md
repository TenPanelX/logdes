local Level = game:GetService("Players").LocalPlayer.Data.Level.Value
local Request = syn.request
local function formatNumber(number)
    local i, k, j = tostring(number):match("(%-?%d?)(%d*)(%.?.*)")
    return i .. k:reverse():gsub("(%d%d%d)", "%1,"):reverse() .. j
end
spawn(
    function()
        while wait(_G.PiwwyBf["Log Delay"]) do
            local World = ""
            local Money = ""
            local Username = game.Players.LocalPlayer.Name
            local Fragment = ""
            local Level = ""
            local Fruit = ""
            local Material = ""
            local Race = ""
            local World = ""
            local FruitMastery = ""
            local Gun = ""
            local RequestgetInventory
            local HttpService = game:GetService("HttpService")
            local Malee = ""
            local Sword = ""
            local Accesorry = ""
            local Awake = ""
            local Combo = ""
            local Evo = ""
            local function notifyCheck(types, ...)
                if types == "Notify" then
                    require(game.ReplicatedStorage.Notification).new(...):Display()
                end
            end
            function format_number_(n)
                local x = n
                local res = x:gsub(",","")
                return tonumber(res)
            end
            
            function foo(n)
                if n >= 10^6 then
                    return string.format("%.2fM", n / 10^6)
                elseif n >= 10^3 then
                    return string.format("%.2fK", n / 10^3)
                else
                    return tostring(n)
                end
            end
            Money = foo(format_number_(formatNumber(game:GetService("Players").LocalPlayer.Data.Beli.Value)))
            Fragment = foo(format_number_(formatNumber(game:GetService("Players").LocalPlayer.Data.Fragments.Value)))
            Race = game:GetService("Players").LocalPlayer.Data.Race.Value
            Level = game:GetService("Players").LocalPlayer.Data.Level.Value
            if
                game.ReplicatedStorage.Remotes.CommF_:InvokeServer("DressrosaQuestProgress", "Dressrosa") == 0 and
                    game.ReplicatedStorage.Remotes.CommF_:InvokeServer("ZQuestProgress", "Zou") == 0
             then
                World = 3
            elseif
                game.ReplicatedStorage.Remotes.CommF_:InvokeServer("DressrosaQuestProgress", "Dressrosa") == 0 and
                    not game.ReplicatedStorage.Remotes.CommF_:InvokeServer("ZQuestProgress", "Zou") and
                    game.ReplicatedStorage.Remotes.CommF_:InvokeServer("ZQuestProgress", "Zou") ~= 0
             then
                World = 2
            else
                World = 1
            end

            RequestgetInventory = game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("getInventory")
            for i, __ in pairs(RequestgetInventory) do
                if __["Type"] == "Sword" then
                    if Sword == "" then
                        if _G.PiwwyBf["Inventory Log Des/Sheet"] and _G.PiwwyBf["OnlyRareItemPlus"]  then
                            if table.find(_G.PiwwyBf["Inventory Log Des/Sheet"], __["Name"]) then
                                Sword = __["Name"] .. " "
                            end
                        else
                            Sword = __["Name"] .. " "
                        end
                    else
                        if _G.PiwwyBf["Inventory Log Des/Sheet"] and _G.PiwwyBf["OnlyRareItemPlus"] then
                            if table.find(_G.PiwwyBf["Inventory Log Des/Sheet"], __["Name"]) then
                                Sword = Sword .. __["Name"] .. " "
                            end
                        else
                            Sword = Sword .. __["Name"] .. " "
                        end
                    end
                end
                if __["Type"] == "Wear" then
                    if Accesorry == "" then
                        Accesorry = __["Name"] .. " "
                    else
                        Accesorry = Accesorry .. __["Name"] .. " "
                    end
                end
                if __["Type"] == "Blox Fruit" then
                    if Fruit == "" then
                        if _G.PiwwyBf["ShowLegendary"] then
                            if __["Rarity"] == 3 then
                                Fruit = __["Name"] .. " "
                            end
                        else
                            Fruit = __["Name"] .. " "
                        end
                    else
                        if _G.PiwwyBf["ShowLegendary"] then
                            if __["Rarity"] == 3 then
                                Fruit = Fruit .. __["Name"] .. " "
                            end
                        else
                            Fruit = Fruit .. __["Name"] .. " "
                        end
                    end
                end
                if __["Type"] == "Material" then
                    if Material == "" then
                        Material = __["Name"] .. " "
                    else
                        Material = Material .. __["Name"] .. "( x" .. __["Count"] .. " )" .. " "
                    end
                end
                if __["Type"] == "Gun" then
                    if Gun == "" then
                        Gun = __["Name"] .. " "
                    else
                        Gun = Gun .. __["Name"] .. " "
                    end
                end
            end
            local args = {
                [1] = "BuyDeathStep",
                [2] = true
            }

            DeathStep = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if DeathStep == 1 then
                HasDeathStep = true
            else
                HasDeathStep = false
            end
            wait(0.2)

            local args = {
                [1] = "BuySharkmanKarate",
                [2] = true
            }

            SharkmanKarate = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if SharkmanKarate == 1 then
                HasSharkmanKarate = true
            end
            wait(0.2)

            local args = {
                [1] = "BuySuperhuman",
                [2] = true
            }

            Superhuman = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if Superhuman == 1 then
                HasSuperhuman = true
            else
                HasSuperhuman = false
            end
            wait(0.2)

            local args = {
                [1] = "BuyElectricClaw",
                [2] = true
            }

            ElectricClaw = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if ElectricClaw == 1 then
                HasElectricClaw = true
            else
                HasElectricClaw = false
            end
            local args = {
                [1] = "BuyDragonTalon",
                [2] = true
            }

            DragonTalon = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if type(DragonTalon) == "number" then
                if DragonTalon == 1 then
                    HasDragonTalon = true
                else
                    HasDragonTalon = false
                end
            end

            local args = {
                [1] = "BuyGodhuman",
                [2] = true
            }
            local FruitName = ""
            Godhuman = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if type(Godhuman) == "number" then
                if Godhuman == 1 then
                    HasGodhuman = true
                else
                    HasGodhuman = false
                end
            end
            if HasDragonTalon then
                Malee = Malee .. "Dragon Talon "
            end
            if HasElectricClaw then
                Malee = Malee .. "Electric Claw "
            end
            if HasSuperhuman then
                Malee = Malee .. "Superhuman "
            end
            if HasSharkmanKarate then
                Malee = Malee .. "Sharkman Karate "
            end
            if HasDeathStep then
                Malee = Malee .. "Death Step "
            end
            if HasGodhuman then
                Malee = Malee .. "God Human"
            end
            for _i, v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                if v:IsA("Tool") then
                    if v.ToolTip == "Blox Fruit" then
                        FruitMastery = v.Level.Value
                        FruitName = v.Name
                    end
                end
            end

            r = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getAwakenedAbilities")
            if r then
                for i, v in pairs(r) do
                    if v["Awakened"] then
                        Awake = Awake .. i .. " "
                    end
                end
            else
                Awake = "None"
            end
            if game:GetService("Players").LocalPlayer.Data.Race:FindFirstChild("Evolved") then
                Evo = ""
            else
                Evo = "No"
            end
            local Payload =
                -- "Level : {l}\nWorld : {w}\nRace: {r}\nEvolved : {re}\nMelee: {m}\nFruit Inventory : {fi}\nSword : {s} \nBeli : {b}\nFragment : {f}\nAwake : {a}\nFruit : {fn}\nFruit Mastery: {fm}"
                "World: {w} Lvl: {l}  Beli: {b} F: {f}\nFruit: {fn} [Mas.{fm}]\nAwaken Skill: {a}\n>>>>>> Melee <<<<<<\n{m}\n>>>>>> Fruit <<<<<<\n{fi}\n>>>>>> Sword <<<<<<\n{s}\n >>>>>> Credit <<<<<< \n Cr.Log Des Make By Piwwy#0909"    
            Payload =
                string.gsub(
                string.gsub(
                    string.gsub(
                        string.gsub(
                            string.gsub(
                                string.gsub(
                                    string.gsub(
                                        string.gsub(
                                            string.gsub(
                                                string.gsub(
                                                    string.gsub(string.gsub(Payload, "{l}", Level), "{r}", Race),
                                                    "{m}",
                                                    Malee
                                                ),
                                                "{fi}",
                                                Fruit
                                            ),
                                            "{s}",
                                            Sword
                                        ),
                                        "{b}",
                                        Money
                                    ),
                                    "{f}",
                                    Fragment
                                ),
                                "{a}",
                                Awake
                            ),
                            "{w}",
                            World
                        ),
                        "{fn}",
                        FruitName
                    ),
                    "{fm}",
                    FruitMastery
                ),
                "{re}",
                Evo
            )

            r =
                Request(
                {
                    Method = "POST",
                    Url = "http://localhost:7963/SetDescription?Account=" .. Username,
                    Body = Payload
                }
            )
        end
    end
)
spawn(
    function()
        while wait(_G.PiwwyBf["Log Delay"]) do
            local Username = game.Players.LocalPlayer.Name
            local args = {
                [1] = "BuyDeathStep",
                [2] = true
            }

            DeathStep = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if DeathStep == 1 then
                HasDeathStep = true
            else
                HasDeathStep = false
            end
            wait(0.2)

            local args = {
                [1] = "BuySharkmanKarate",
                [2] = true
            }

            SharkmanKarate = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if SharkmanKarate == 1 then
                HasSharkmanKarate = true
            end
            wait(0.2)

            local args = {
                [1] = "BuySuperhuman",
                [2] = true
            }

            Superhuman = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if Superhuman == 1 then
                HasSuperhuman = true
            else
                HasSuperhuman = false
            end
            wait(0.2)

            local args = {
                [1] = "BuyElectricClaw",
                [2] = true
            }

            ElectricClaw = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if ElectricClaw == 1 then
                HasElectricClaw = true
            else
                HasElectricClaw = false
            end
            local args = {
                [1] = "BuyDragonTalon",
                [2] = true
            }

            DragonTalon = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if type(DragonTalon) == "number" then
                if DragonTalon == 1 then
                    HasDragonTalon = true
                else
                    HasDragonTalon = false
                end
            end

            local args = {
                [1] = "BuyGodhuman",
                [2] = true
            }
            local FruitName = ""
            Godhuman = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            if type(Godhuman) == "number" then
                if Godhuman == 1 then
                    HasGodhuman = true
                else
                    HasGodhuman = false
                end
            end
            
            local Ml = 0
           if HasDragonTalon then
            Ml = Ml + 1
            end
           if HasElectricClaw then
            Ml = Ml + 1
            end
           if HasSuperhuman then 
            Ml = Ml +1
            end
           if HasSharkmanKarate then
            Ml = Ml +1
            end
           if HasDeathStep then
            Ml = Ml +1
           end
           if HasGodhuman then
               Ml = "God"
               end
            _G.Pro_Inventory_Kaitun = true
            if _G.Pro_Inventory_Kaitun then 
				Payload = ""
                if HasGodhuman then
                    Payload = Payload .. Ml.." | "
                    else
                    Payload = Payload .. Ml.."/6".." | "
              end
		
						local MyFruit = game:GetService("Players").LocalPlayer.Data.DevilFruit.Value
						if MyFruit == "Dark-Dark" then
						    CurrentFruitName = "Dark"
						elseif MyFruit == 'Flame-Flame' then
						     CurrentFruitName = "Flame"
						elseif MyFruit == 'Quake-Quake' then
						     CurrentFruitName = "Quake"
						elseif MyFruit == 'Human-Human: Buddha' then
						     CurrentFruitName = "Buddha"
						elseif MyFruit == 'Sand-Sand' then
						     CurrentFruitName = "Sand"
						elseif MyFruit == 'Light-Light' then
						     CurrentFruitName = "Light"
						elseif MyFruit == 'Magma-Magma' then
						     CurrentFruitName = "Magma"
						elseif MyFruit == 'Bird-Bird: Phoenix' then
						    CurrentFruitName = "Phoenix"
						elseif MyFruit == 'Rumble-Rumble' then
						    CurrentFruitName = "Rumble"
						elseif MyFruit == 'Dough-Dough' then
						    CurrentFruitName = "Dough"
						elseif MyFruit == 'Dragon-Dragon' then
						    CurrentFruitName = "Dragon"
						 elseif MyFruit == 'Leopard-Leopard' then
						    CurrentFruitName = "Leopard"
						 elseif MyFruit == 'Ice-Ice' then
					      CurrentFruitName = "Ice"
						 else
					        CurrentFruitName = "Not Have in Our List"
						 	end
					HHH = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getAwakenedAbilities")
    if HHH then
        S = 0
            for i, v in pairs(HHH) do
                if v["Awakened"] then
                 S = S + 1
                    end
            end
            else
                S = 'No'
            end
                        Payload = Payload .."[".. S .."]: " ..CurrentFruitName.." |"
                        RequestgetInventory = game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("getInventory")
                        for i,x in pairs(RequestgetInventory) do
                             if x["Type"] == "Sword" then
                                 if x["Name"] == "Cursed Dual Katana" then
                                   CDKYed = true
                                   end
                                 if x["Name"] == "Hallow Scythe" then
                                    HSYed = true
                                    end
                                 if x["Name"] == "Dark Dagger" then
                                     DDGYed = true
                                     end
                                 if x["Name"] == "Yama" then
                                  YMYed = true
                                  end
                                 if x["Name"] == "Tushita" then
                                  TSYed = true
                                  end
                                 if x["Name"] == "True Triple Katana" then
                                 TTKYed = true
                                 end
                               
                                  if x["Name"] == "Canvander" then
                                     CVDYed = true
                                 end
                                 
                                 
                     
                             end
                    end
                       RequestgetInventory = game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("getInventory")
                        for i,x in pairs(RequestgetInventory) do
                             if x["Type"] == "Gun" then
                                 if x["Name"] == "Soul Guitar" then
                                   SGYed = true
                                
                                 end
                             end
                        end
end                
                        
local Inventory = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")
function GetMasterySword(Name)
    for i,v in pairs(Inventory) do
        if v.Type == "Sword" then
            if v.Name == Name then
                return v.Mastery
            end
        end
    end
end
local Inventory = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")
function GetMasGun(Name)
    for i,v in pairs(Inventory) do
        if v.Type == "Gun" then
            if v.Name == Name then
                return v.Mastery
            end
        end
    end
end                 if _G.PiwwyBf["Show Mastery"] then
                        if CDKYed then
                        Payload = Payload .." CDK: "..GetMasterySword("Cursed Dual Katana").." |"
                        end
                        if HsYed then
                            Payload = Payload .." HS: "..GetMasterySword("Hallow Scythe").." |"
                            end
                        if SGYed then
                            Payload = Payload .." SG: "..GetMasGun("Soul Guitar").." |"
                            end
                        if DDGYed then
                             Payload = Payload .." DDG: "..GetMasterySword("Dark Dagger").." |"
                             end
                        if YMYed then
                            Payload = Payload .." YM: "..GetMasterySword("Yama").." |"
                            end
                        if TSYed then
                            Payload = Payload .." TS: "..GetMasterySword("Tushita").." |"
                            end
                        if TTKYed then
                            Payload = Payload .." TTK: "..GetMasterySword("True Triple Katana")
                            end
                        else
                            if CDKYed then
                                Payload = Payload .." CDK | "
                                end
                                if HsYed then
                                    Payload = Payload .." HS | "
                                    end
                                if SGYed then
                                    Payload = Payload .." SG | "
                                    end
                                if DDGYed then
                                     Payload = Payload .." DDG | "
                                     end
                                if YMYed then
                                    Payload = Payload .." YM | "
                                    end
                                if TSYed then
                                    Payload = Payload .." TS | "
                                    end
                                if TTKYed then
                                    Payload = Payload .." TTK "
                                    end
                        end
            r =
                Request(
                {
                    Method = "POST",
                    Url = "http://localhost:7963/SetAlias?Account=" .. Username,
                    Body = Payload
                }
            )
        end
    end
)
Nexus_Version = 101
loadstring(
    game:HttpGet "https://raw.githubusercontent.com/ic3w0lf22/Roblox-Account-Manager/master/RBX%20Alt%20Manager/Nexus/Nexus.lua"
)()
task.spawn(
    function()
        Nexus:Connect()
    end
)
