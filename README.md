if game.PlaceId == 85896571713843 then 
  local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/jensonhirst/Orion/main/source')))()
  local Window = OrionLib:MakeWindow({Name = "🐰 Bubble Gum Simulator INFINITO", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})
  
--Value
_G.AutoBubble = true 
_G.GiantChest = true
_G.VoidChest = true
_G.AutoPets = true
_G.AutoSell = true
_G.AutoHatch = true
_G.selectEgg = "Bunny Egg"
  
--Functions
  function AutoBubble()
    while _G.AutoBubble == true do 
      game:GetService("ReplicatedStorage").Shared.Framework.Network.Remote.Event:FireServer("BlowBubble")
      wait(0.0000000001)
    end
  end
  
  function AutoSell()
    while _G.AutoSell == true do
      game:GetService("ReplicatedStorage").Shared.Framework.Network.Remote.Event:FireServer("SellBubble")
      wait(0.000000000001)
    end
  end  
  
  function AutoChest()
    while _G.AutoChest == true do
      game:GetService("ReplicatedStorage").Shared.Framework.Network.Remote.Event:FireServer("ClaimChest","Giant Chest",true)
      wait(0.00000000001)
    end
  end
  
  function VoidChest()
    while _G.VoidChest == true do
      game:GetService("ReplicatedStorage").Shared.Framework.Network.Remote.Event:FireServer("ClaimChest","Void Chest",true)
      wait(0.00000000001)
    end
  end
  
  function AutoPets()
    while _G.AutoPets == true do
      game:GetService("ReplicatedStorage").Shared.Framework.Network.Remote.Event:FireServer("EquipBestPets")
      wait(15)
    end
  end
  
  function AutoHatch()
    while _G.AutoHatch == true do
      game:GetService("ReplicatedStorage").Shared.Framework.Network.Remote.Event:FireServer("HatchEgg",_G.selectEgg,4)
      wait(0.00000000001)
    end
  end
  
  function TeleportEvent()
      game:GetService("ReplicatedStorage").Shared.Framework.Network.Remote.Event:FireServer("Teleport","Workspace.Event.Portal.Spawn")
      wait(0.0000000000001)
    end
  
--Tabs
local EventTab = Window:MakeTab({
	Name = "Event",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})
  
  local MainTab = Window:MakeTab({
	Name = "Main",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})
  
local ShoppingTab = Window:MakeTab({
	Name = "Shopping",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})  
  
--Seçoes
local Section = MainTab:AddSection({
	Name = "Auto-Farm"
})
  
MainTab:AddToggle({
   	Name = "AutoBubble",
   	Default = false,
   	Callback = function(Value)
   		_G.AutoBubble = Value
   	  AutoBubble()
	end    
})
  
MainTab:AddToggle({
   	Name = "AutoSell",
   	Default = false,
   	Callback = function(Value)
   		_G.AutoSell = Value
	     AutoSell()
	end    
})  
  
  local Section = MainTab:AddSection({
	Name = "Auto-Chests"
})
  
MainTab:AddToggle({
   	Name = "Giant Chest",
   	Default = false,
   	Callback = function(Value)
  		_G.AutoChest = Value
	    AutoChest()
	end    
})
  
MainTab:AddToggle({
	   Name = "Void Chest",
   	Default = false,
   	Callback = function(Value)
   		_G.VoidChest = Value
	     VoidChest()
	end    
})
  
local Section = MainTab:AddSection({
	Name = "Auto-Equip"
})  
  
 MainTab:AddToggle({
	   Name = "EquipBestPets",
   	Default = false,
   	Callback = function(Value)
   		_G.AutoPets = Value
	     AutoPets()
	end    
})
  
local Section = EventTab:AddSection({
	Name = "Event"
})
  
EventTab:AddButton({
   	Name = "Teleport Event",
	   Callback = function()
      		TeleportEvent()
	  
  	end    
})
  
local Section = EventTab:AddSection({
	Name = "Eggs"
})  
  
EventTab:AddLabel("Voce precisa estar perto do egg.")  
  
EventTab:AddDropdown({
	Name = "select Egg",
	Default = "BunnyEgg",
	Options = {"Bunny Egg", "Pastel Egg"},
	Callback = function(Value)
	  _G.selectEgg = Value
	  print(_G.selectEgg)
	end    
})
  
EventTab:AddToggle({
	   Name = "Auto Hatch",
   	Default = false,
   	Callback = function(Value)
		   _G.AutoHatch = Value
	     AutoHatch()
   	end
})
  
end  
OrionLib:Init()
