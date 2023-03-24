



local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local ImageLabel = Instance.new("ImageLabel")
local UICorner = Instance.new("UICorner")
local UICorner_2 = Instance.new("UICorner")
local Drop_Shadow = Instance.new("ImageLabel")
local Drop_Shadow_2 = Instance.new("ImageLabel")
local TextLabel = Instance.new("TextLabel")

--Properties:

ScreenGui.Parent = game.CoreGui

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame.Position = UDim2.new(0.437397063, 0, 0.345808387, 0)
Frame.Size = UDim2.new(0, 100, 0, 100)
Frame.Active = true

ImageLabel.Parent = Frame
ImageLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
ImageLabel.Size = UDim2.new(0, 100, 0, 100)
ImageLabel.Image = "http://www.roblox.com/asset/?id=12802092295"

UICorner.Parent = ImageLabel

UICorner_2.Parent = Frame

Drop_Shadow.Name = "Drop_Shadow"
Drop_Shadow.Parent = Frame
Drop_Shadow.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Drop_Shadow.BackgroundTransparency = 1.000
Drop_Shadow.Position = UDim2.new(0, -36, 0, -37)
Drop_Shadow.Size = UDim2.new(1.73263621, 1, 1.7637614, 1)
Drop_Shadow.ZIndex = -5
Drop_Shadow.Image = "rbxassetid://1113384364"
Drop_Shadow.ImageTransparency = 0.200
Drop_Shadow.ScaleType = Enum.ScaleType.Slice
Drop_Shadow.SliceCenter = Rect.new(50, 50, 50, 50)

Drop_Shadow_2.Name = "Drop_Shadow"
Drop_Shadow_2.Parent = Frame
Drop_Shadow_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Drop_Shadow_2.BackgroundTransparency = 1.000
Drop_Shadow_2.Position = UDim2.new(0, -36, 0, -37)
Drop_Shadow_2.Size = UDim2.new(1.73263621, 1, 1.7637614, 1)
Drop_Shadow_2.ZIndex = -5
Drop_Shadow_2.Image = "rbxassetid://1113384364"
Drop_Shadow_2.ImageTransparency = 0.200
Drop_Shadow_2.ScaleType = Enum.ScaleType.Slice
Drop_Shadow_2.SliceCenter = Rect.new(50, 50, 50, 50)

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.Position = UDim2.new(-0.180000007, 0, 1, 0)
TextLabel.Size = UDim2.new(0, 135, 0, 50)
TextLabel.Font = Enum.Font.SourceSansBold
TextLabel.Text = "Loading . . ."
TextLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.TextScaled = true
TextLabel.TextSize = 14.000
TextLabel.TextWrapped = true


wait(4.5)


Frame.Visible = false



--Made By S.#0094


-- Bacon X Version 2

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Bacon X | Da hood", "Serpent")


--Main

local Main = Window:NewTab("Main")
local MainSection = Main:NewSection("Misc")


MainSection:NewButton("Fly X", "Fly Lets U Fly Around The Map Made By Bacon X", function()
    
 game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Fly Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})

local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

repeat wait() 
		until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Head") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid") 
		local mouse = game.Players.LocalPlayer:GetMouse() 
		repeat wait() until mouse
		local plr = game.Players.LocalPlayer 
		local torso = plr.Character.Head 
		local flying = false
		local deb = true 
		local ctrl = {f = 0, b = 0, l = 0, r = 0} 
		local lastctrl = {f = 0, b = 0, l = 0, r = 0} 
		local maxspeed = 5000
		local speed = 5000 
	
		function Fly() 
			local bg = Instance.new("BodyGyro", torso) 
			bg.P = 9e4 
			bg.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
			bg.cframe = torso.CFrame 
			local bv = Instance.new("BodyVelocity", torso) 
			bv.velocity = Vector3.new(0,0.1,0) 
			bv.maxForce = Vector3.new(9e9, 9e9, 9e9) 
			repeat wait() 
				plr.Character.Humanoid.PlatformStand = true 
				if ctrl.l + ctrl.r ~= 100000 or ctrl.f + ctrl.b ~= 10000 then 
					speed = speed+.0+(speed/maxspeed) 
					if speed > maxspeed then 
						speed = maxspeed 
					end 
				elseif not (ctrl.l + ctrl.r ~= 5 or ctrl.f + ctrl.b ~= 5) and speed ~= 5 then 
					speed = speed-5
					if speed > 5 then 
						speed = -2 
					end 
				end 
				if (ctrl.l + ctrl.r) ~= 5 or (ctrl.f + ctrl.b) ~= 5 then 
					bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
					lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r} 
				elseif (ctrl.l + ctrl.r) == 5 and (ctrl.f + ctrl.b) == 5 and speed ~= 5 then 
					bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
				else 
					bv.velocity = Vector3.new(0,0.1,0) 
				end 
				bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0) 
			until not flying 
			ctrl = {f = 0, b = 0, l = 0, r = 0} 
			lastctrl = {f = 0, b = 0, l = 0, r = 0} 
			speed = 5 
			bg:Destroy() 
			bv:Destroy() 
			plr.Character.Humanoid.PlatformStand = false 
		end 
		mouse.KeyDown:connect(function(key) 
			if key:lower() == "x" then 
				if flying then flying = false 
				else 
					flying = true 
					Fly() 
				end 
			elseif key:lower() == "w" then 
				ctrl.f = 45
			elseif key:lower() == "s" then 
				ctrl.b = -45 
			elseif key:lower() == "a" then 
				ctrl.l = -45 
			elseif key:lower() == "d" then 
				ctrl.r = 45
			end 
		end) 
		mouse.KeyUp:connect(function(key) 
			if key:lower() == "w" then 
				ctrl.f = 0
			elseif key:lower() == "s" then 
				ctrl.b = 0
			elseif key:lower() == "a" then 
				ctrl.l = 0
			elseif key:lower() == "d" then 
				ctrl.r = 0
			end 
		end)
		Fly()
end)



MainSection:NewButton("Fast Fly X", "faster fly", function()
    
    	 game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Fast Fly Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})

local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

repeat wait() 
		until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Head") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid") 
		local mouse = game.Players.LocalPlayer:GetMouse() 
		repeat wait() until mouse
		local plr = game.Players.LocalPlayer 
		local torso = plr.Character.Head 
		local flying = false
		local deb = true 
		local ctrl = {f = 0, b = 0, l = 0, r = 0} 
		local lastctrl = {f = 0, b = 0, l = 0, r = 0} 
		local maxspeed = 5000
		local speed = 5000 
	
		function Fly() 
			local bg = Instance.new("BodyGyro", torso) 
			bg.P = 9e4 
			bg.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
			bg.cframe = torso.CFrame 
			local bv = Instance.new("BodyVelocity", torso) 
			bv.velocity = Vector3.new(0,0.1,0) 
			bv.maxForce = Vector3.new(9e9, 9e9, 9e9) 
			repeat wait() 
				plr.Character.Humanoid.PlatformStand = true 
				if ctrl.l + ctrl.r ~= 100000 or ctrl.f + ctrl.b ~= 10000 then 
					speed = speed+.0+(speed/maxspeed) 
					if speed > maxspeed then 
						speed = maxspeed 
					end 
				elseif not (ctrl.l + ctrl.r ~= 5 or ctrl.f + ctrl.b ~= 5) and speed ~= 5 then 
					speed = speed-5
					if speed > 5 then 
						speed = -2 
					end 
				end 
				if (ctrl.l + ctrl.r) ~= 5 or (ctrl.f + ctrl.b) ~= 5 then 
					bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
					lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r} 
				elseif (ctrl.l + ctrl.r) == 5 and (ctrl.f + ctrl.b) == 5 and speed ~= 5 then 
					bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
				else 
					bv.velocity = Vector3.new(0,0.1,0) 
				end 
				bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0) 
			until not flying 
			ctrl = {f = 0, b = 0, l = 0, r = 0} 
			lastctrl = {f = 0, b = 0, l = 0, r = 0} 
			speed = 20
			bg:Destroy() 
			bv:Destroy() 
			plr.Character.Humanoid.PlatformStand = false 
		end 
		mouse.KeyDown:connect(function(key) 
			if key:lower() == "x" then 
				if flying then flying = false 
				else 
					flying = true 
					Fly() 
				end 
			elseif key:lower() == "w" then 
				ctrl.f = 45
			elseif key:lower() == "s" then 
				ctrl.b = -45 
			elseif key:lower() == "a" then 
				ctrl.l = -45 
			elseif key:lower() == "d" then 
				ctrl.r = 45
			end 
		end) 
		mouse.KeyUp:connect(function(key) 
			if key:lower() == "w" then 
				ctrl.f = 0
			elseif key:lower() == "s" then 
				ctrl.b = 0
			elseif key:lower() == "a" then 
				ctrl.l = 0
			elseif key:lower() == "d" then 
				ctrl.r = 0
			end 
		end)
		Fly()

end)


local Player = Window:NewTab("Reach PATCHED")
local PlayerSection = Player:NewSection("Reach")



PlayerSection:NewButton("Fist Reach", "Gives U Fist Reach", function()
    
   game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Fist Reach Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
      local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
      	
      		game:GetService('RunService'):BindToRenderStep("Reach", 0 , function(value)
                local success, err = pcall(function()
                    if game.Players.LocalPlayer.Character.BodyEffects.Attacking.Value == true then
                        for i,v in pairs(game:GetService('Players'):GetChildren()) do
                            if (v.Character.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.LeftHand.Position).Magnitude <= 50 then
                                if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool") then
                                    if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool"):FindFirstChild('Handle') then
                                        firetouchinterest(game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Handle, v.Character.UpperTorso, 0)
                                    else
                                        firetouchinterest(game.Players.LocalPlayer.Character['RightHand'], v.Character.UpperTorso, 0)
                                        firetouchinterest(game.Players.LocalPlayer.Character['LeftHand'], v.Character.UpperTorso, 0)
                                        firetouchinterest(game.Players.LocalPlayer.Character['RightFoot'], v.Character.UpperTorso, 0)
                                        firetouchinterest(game.Players.LocalPlayer.Character['LeftFoot'], v.Character.UpperTorso, 0)
                                        firetouchinterest(game.Players.LocalPlayer.Character['RightLowerLeg'], v.Character.UpperTorso, 0)
                                        firetouchinterest(game.Players.LocalPlayer.Character['LeftLowerLeg'], v.Character.UpperTorso, 0)
                                    end
                                end
                            end
                        end
                    end
                    end)
                end)
end)


PlayerSection:NewButton("Bat Reach", "Gives U Reach For Bat Tool", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Bat Reach Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Backpack["[Bat]"].Handle.Size = Vector3.new(50, 50, 50)
end)



MainSection:NewButton("Anti Fling", "Now Exploiter Cant Fling ", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Anti Fling Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    loadstring(game:HttpGet('https://pastebin.com/raw/hKfDWcJw'))();
end)


MainSection:NewButton("Anti Afk", "It Doesnt Let Roblox Kick U", function()
    
    	 game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Anti Afk Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    		
    			local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    				
    			for i,v in pairs(getconnections(game:GetService("Players").LocalPlayer.Idled)) do
    v:Disable()
end
end)


PlayerSection:NewButton("SledgeHammer Reach", "Gives U tool Reach", function()
    
    game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "SledgeHammer Reach Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Backpack["[SledgeHammer]"].Handle.Size = Vector3.new(50, 50, 50)
end)



PlayerSection:NewButton("Shovel Reach", "Gives Tool Reach", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Shovel Reach Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Backpack["[Shovel]"].Handle.Size = Vector3.new(50, 50, 50)
end)


PlayerSection:NewButton("Knife Reach", "Reach For Ur Knife", function()
    
 game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Knife Reach Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Backpack["[Knife]"].Handle.Size = Vector3.new(50, 50, 50)
end)



local Human = Window:NewTab("Fun Stuff")
local HumanSection = Human:NewSection("Fun Stuff")


PlayerSection:NewButton("Stop Sign Reach", "Gives Ur Tool Reach", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Stop Sign Reach Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Backpack["[StopSign]"].Handle.Size = Vector3.new(50, 50, 50)
end)


HumanSection:NewButton("Bike Fly", "Flying while On Bike", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Bike Fly Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    loadstring(game:HttpGetAsync("https://paste.website/p/a07c1662-6e1d-48fe-aa15-e3341d607965.txt"))()
end)


HumanSection:NewButton("Hulk Powers", "Makes U Hulk", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Hulk Powers Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    local lp = game:GetService"Players".LocalPlayer
local SuperSpeed = Instance.new("IntValue",lp.Character.BodyEffects.Movement);SuperSpeed.Name = "SuperSpeed"
local HulkJump = Instance.new("IntValue",lp.Character.BodyEffects.Movement);HulkJump.Name = "HulkJump"
end)


HumanSection:NewButton("Fake Ban Menu", "Troll on Screen share", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Fake Ban Menu Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Manny72911/modmenu/main/modmenu"))()
end)


MainSection:NewButton("Anti Stomp", "Cant Get Stomped", function()

     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Anti Stomp Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
        

	local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
while true do
	
	wait(.1)
	local Players = game:GetService("Players")
	
		if Players.LocalPlayer.Character.Humanoid.Health <= 60 then
	  game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-628.166382, -490.203003, -998.47583, -0.990315616, -0.0130356653, 0.138220921, 1.04504627e-08, 0.995582223, 0.0938937962, -0.138834253, 0.0929844975, -0.9969896580)
	   end
	end

end)




PlayerSection:NewButton("Free Fist (T)", "move fist", function()
    game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Free Fist Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
   local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
   
    -- // Variables
	local localPlayer       = game:GetService("Players").LocalPlayer
	local localCharacter    = localPlayer.Character
	local Mouse             = localPlayer:GetMouse()
	local FistControl       = false
	local LeftFist          = localCharacter.LeftHand
	local RightFist         = localCharacter.RightHand

	-- // Services
	local uis = game:GetService("UserInputService")

	-- // Coroutine Loop + Functions
	local loopFunction = function()
		LeftFist.CFrame  = CFrame.new(Mouse.Hit.p)
		RightFist.CFrame = CFrame.new(Mouse.Hit.p)
	end

	local Loop

	local Start = function()
		Loop = game:GetService("RunService").Heartbeat:Connect(loopFunction)
	end

	local Pause = function()
		Loop:Disconnect()
	end

	-- // Hotkeys
	uis.InputBegan:connect(function(Key)
		if (Key.KeyCode == Enum.KeyCode.T) then
			if (FistControl == false) then
				FistControl = true
				Start()
				pcall(function()
					localCharacter.RightHand.RightWrist:Remove()
					localCharacter.LeftHand.LeftWrist:Remove()
				end)
			elseif (FistControl == true) then
				FistControl = false
				Pause()
				local rightwrist  = Instance.new("Motor6D")
				rightwrist.Name   = "RightWrist"
				rightwrist.Parent = localCharacter.RightHand
				rightwrist.C0     = CFrame.new(1.18422506e-07, -0.5009287, -6.81715525e-18, 1, 0, 0, 0, 1, 0, 0, 0, 1)
				rightwrist.C1     = CFrame.new(3.55267503e-07, 0.125045404, 5.92112528e-08, 1, 0, 0, 0, 1, 0, 0, 0, 1)
				rightwrist.Part0  = localCharacter.RightLowerArm
				rightwrist.Part1  = localCharacter.RightHand

				local leftwrist   = Instance.new("Motor6D")
				leftwrist.Name    = "LeftWrist"
				leftwrist.Parent  = localCharacter.LeftHand
				leftwrist.C0      = CFrame.new(0.000475466368, -0.5009287, 7.59417072e-20, 1, 0, 0, 0, 1, 0, 0, 0, 1)
				leftwrist.C1      = CFrame.new(0.000475821638, 0.125045404, 5.92112528e-08, 1, 0, 0, 0, 1, 0, 0, 0, 1)
				leftwrist.Part0   = localCharacter.LeftLowerArm
				leftwrist.Part1   = localCharacter.LeftHand
			end
		end
	end)
end)



local monkey = Window:NewTab("God Mode PATCHED")
local monkeySection = monkey:NewSection("God")


monkeySection:NewButton("God Mode NO GUNS OR FIST", "Invinsible", function()
    	
    	
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "God Mode Loaded *useless", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    local Client = game:GetService"Players".LocalPlayer

	function Godmode()
		local Attacking = Client.Character:FindFirstChild"BodyEffects".Attacking

		if Attacking then
			Attacking:Destroy()
		end
	end
	Godmode()

	Client.CharacterAdded:Connect(function()
		wait(1)

		Godmode()
	end)
end)



local scriptware = Window:NewTab("Aimlock")
local scriptwareSection = scriptware:NewSection("Streamable Lock")


scriptwareSection:NewButton("Aimlock", "lock onto anyplayer", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Streamable Lock Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    
    local hotkey = "t" -- toggle key
local mouse = game.Players.LocalPlayer:GetMouse()



mouse.KeyDown:Connect(function(key)
if key == hotkey then
if getgenv().ValiantAimHacks.SilentAimEnabled == true then
 getgenv().ValiantAimHacks.SilentAimEnabled = false
else
getgenv().ValiantAimHacks.SilentAimEnabled = true
end
end
end)


-- // Services
local Players = game:GetService("Players")

-- // Vars
local LocalPlayer = Players.LocalPlayer
local accomidationfactor = 0.12567724521

-- // Silent Aim Module
local SilentAim = loadstring(game:HttpGet("https://pastebin.com/raw/2f0mGbMP"))()
SilentAim.TeamCheck = false
-- // Metatable vars
local mt = getrawmetatable(game)
local backupindex = mt.__index
setreadonly(mt, false)

-- // Check if player is down
SilentAim.checkSilentAim = function()
    local checkA = (SilentAim.SilentAimEnabled == true and SilentAim.Selected ~= LocalPlayer)
    local playerCharacter = SilentAim.Selected.Character
    local daHood = (playerCharacter.BodyEffects["K.O"].Value == false or playerCharacter:FindFirstChild("GRABBING_CONSTRAINT") ~= nil)

    return (checkA and daHood)
end

-- // Hook
mt.__index = newcclosure(function(t, k)
    if (t:IsA("Mouse") and (k == "Hit")) then
        print(t, k)
        local CPlayer = SilentAim.Selected
        if (SilentAim.checkSilentAim()) then
            if (CPlayer.Character:FindFirstChild("HumanoidRootPart")) then
                return {p=(CPlayer.Character.HumanoidRootPart.CFrame.p+(CPlayer.Character.HumanoidRootPart.Velocity*accomidationfactor))}
            end
        end
    end
    return backupindex(t, k)
end)

-- // Revert
setreadonly(mt, true)
getgenv().ValiantAimHacks.FOV = 100
end)


scriptwareSection:NewButton("Anti Lock", "No one Can Lock Onto U", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Anti Lock Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    
getgenv().Underground = true 
getgenv().UndergroundAmount = 90

game:GetService("RunService").heartbeat:Connect(function()
    if getgenv().Underground ~= false then 
    local vel = game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity
    game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(0,-         getgenv().UndergroundAmount,0) 
    game:GetService("RunService").RenderStepped:Wait()
    game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = vel
    end 
end)
end)


HumanSection:NewButton("Headless", "Gives U headless not FE", function()
    	
    	 game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Headless NO FE Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    	
    	
    	local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    	
    	game.Players.LocalPlayer.Character.Head.Transparency = 1
	game.Players.LocalPlayer.Character.Head.Transparency = 1
	for i,v in pairs(game.Players.LocalPlayer.Character.Head:GetChildren()) do
		if (v:IsA("Decal")) then
			v.Transparency = 1
		end
	end
end)



HumanSection:NewButton("Korblox", "Fake Korblox Not FE", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Korblox NO FE Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    
    
    local ply = game.Players.LocalPlayer
	local chr = ply.Character
	chr.RightLowerLeg.MeshId = "902942093"
	chr.RightLowerLeg.Transparency = "1"
	chr.RightUpperLeg.MeshId = "http://www.roblox.com/asset/?id=902942096"
	chr.RightUpperLeg.TextureID = "http://roblox.com/asset/?id=902843398"
	chr.RightFoot.MeshId = "902942089"
	chr.RightFoot.Transparency = "1"
end)


HumanSection:NewButton("Korblox FE", "fe korblox", function()
    
    game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Korblox FE Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    
    local Leg = 'Right'
 
local plr = game.Players.LocalPlayer
local char = plr.Character
 
if char.Humanoid.RigType == Enum.HumanoidRigType.R15 then
   char[Leg..'UpperLeg']:Destroy()
   char[Leg..'LowerLeg']:Destroy()
   char[Leg..'Foot']:Destroy()
else
   char[Leg..' Leg']:Destroy()
end
end)



local TP = Window:NewTab("Teleport")
local TPSection = TP:NewSection("Teleports")


TPSection:NewButton("Db Teleport", "tp db", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Db Teleport Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1043.91, 21.7575, -258.886)
end)



TPSection:NewButton("Rev Teleport", "tp rev", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Rev Teleport Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-642.597, 21.7575, -123.507)
end)



TPSection:NewButton("UFO Teleport", "tp ufo", function()
    
    game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "UFO Teleport Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(81.618, 139.007, -682.725)
end)


TPSection:NewButton("DownHill Guns Teleport", "Tp Downhill", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Downhill Gunz Teleport", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-575.928, 8.32231, -729.556)
end)


TPSection:NewButton("Bank Teleport", "Tp Bank", function()
    
    game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Bank Teleport Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-431.683, 22.9708, -284.988)
end)


TPSection:NewButton("Uphill Guns Teleport", "tp uphill", function()
    
    game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Uphill Gunz Teleport Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(479.781, 48.078, -619.247)
end)


TPSection:NewButton("Admin Base Teleport", "tp admin base", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Admin Base Teleport Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-869.554, -38.3917, -598.2)    
end)


TPSection:NewButton("HighSchool Teleport", "tp highschool", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Highschool Teleport Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-654.25, 21.8825, 281)    
end)


TPSection:NewButton("Casino Teleport", "tp casino", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Casino Teleport Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-992.894, 24.6075, -157.529)    
end)




scriptwareSection:NewButton("Esp", "u can see through walls", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "ESP Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    --[[
A distribution of https://wearedevs.net/scripts
Created August 17, 2021, Last updated August 17, 2021

Description: Draws boxes around each player.

Credits to "Real Panda" for their ESP library

Instruction: Edit the settings as desired below and execute the script.

Settings: 
Replace "nil" with "true" to enable the setting, or "false" to disable the setting. Without the quotes. 
If you do not change "nil", the defaults will take place.
]]
_G.WRDESPEnabled = nil --Enables the ESP (Defaults to true)
_G.WRDESPBoxes = nil --Draws boxes around other players (Defaults to true)
_G.WRDESPTeamColors = nil --Distinguish different teams by their team color. If the game sets one. (Defaults to true)
_G.WRDESPTracers = nil --Displays lines leading to other players (Defaults to false)
_G.WRDESPNames = nil --Displays the names of the players within the ESP box (Defaults to true)

--Dont edit below

--Only ever load the script once
if not _G.WRDESPLoaded then    
    ----[[ First- Load Kiriot ESP Library ]]----

    --Settings--
    local ESP = {
        Enabled = false,
        Boxes = false,
        BoxShift = CFrame.new(0,-1.5,0),
        BoxSize = Vector3.new(4,6,0),
        Color = Color3.fromRGB(255, 170, 0),
        FaceCamera = false,
        Names = true,
        TeamColor = true,
        Thickness = 2,
        AttachShift = 1,
        TeamMates = true,
        Players = true,
        
        Objects = setmetatable({}, {__mode="kv"}),
        Overrides = {}
    }

    --Declarations--
    local cam = workspace.CurrentCamera
    local plrs = game:GetService("Players")
    local plr = plrs.LocalPlayer
    local mouse = plr:GetMouse()

    local V3new = Vector3.new
    local WorldToViewportPoint = cam.WorldToViewportPoint

    --Functions--
    local function Draw(obj, props)
        local new = Drawing.new(obj)
        
        props = props or {}
        for i,v in pairs(props) do
            new[i] = v
        end
        return new
    end

    function ESP:GetTeam(p)
        local ov = self.Overrides.GetTeam
        if ov then
            return ov(p)
        end
        
        return p and p.Team
    end

    function ESP:IsTeamMate(p)
        local ov = self.Overrides.IsTeamMate
        if ov then
            return ov(p)
        end
        
        return self:GetTeam(p) == self:GetTeam(plr)
    end

    function ESP:GetColor(obj)
        local ov = self.Overrides.GetColor
        if ov then
            return ov(obj)
        end
        local p = self:GetPlrFromChar(obj)
        return p and self.TeamColor and p.Team and p.Team.TeamColor.Color or self.Color
    end

    function ESP:GetPlrFromChar(char)
        local ov = self.Overrides.GetPlrFromChar
        if ov then
            return ov(char)
        end
        
        return plrs:GetPlayerFromCharacter(char)
    end

    function ESP:Toggle(bool)
        self.Enabled = bool
        if not bool then
            for i,v in pairs(self.Objects) do
                if v.Type == "" then --fov circle etc
                    if v.Temporary then
                        v:Remove()
                    else
                        for i,v in pairs(v.Components) do
                            v.Visible = false
                        end
                    end
                end
            end
        end
    end

    function ESP:GetBox(obj)
        return self.Objects[obj]
    end

    function ESP:AddObjectListener(parent, options)
        local function NewListener(c)
            if type(options.Type) == "string" and c:IsA(options.Type) or options.Type == nil then
                if type(options.Name) == "string" and c.Name == options.Name or options.Name == nil then
                    if not options.Validator or options.Validator(c) then
                        local box = ESP:Add(c, {
                            PrimaryPart = type(options.PrimaryPart) == "string" and c:WaitForChild(options.PrimaryPart) or type(options.PrimaryPart) == "function" and options.PrimaryPart(c),
                            Color = type(options.Color) == "function" and options.Color(c) or options.Color,
                            ColorDynamic = options.ColorDynamic,
                            Name = type(options.CustomName) == "function" and options.CustomName(c) or options.CustomName,
                            IsEnabled = options.IsEnabled,
                            RenderInNil = options.RenderInNil
                        })
                        --TODO: add a better way of passing options
                        if options.OnAdded then
                            coroutine.wrap(options.OnAdded)(box)
                        end
                    end
                end
            end
        end

        if options.Recursive then
            parent.DescendantAdded:Connect(NewListener)
            for i,v in pairs(parent:GetDescendants()) do
                coroutine.wrap(NewListener)(v)
            end
        else
            parent.ChildAdded:Connect(NewListener)
            for i,v in pairs(parent:GetChildren()) do
                coroutine.wrap(NewListener)(v)
            end
        end
    end

    local boxBase = {}
    boxBase.__index = boxBase

    function boxBase:Remove()
        ESP.Objects[self.Object] = nil
        for i,v in pairs(self.Components) do
            v.Visible = false
            v:Remove()
            self.Components[i] = nil
        end
    end

    function boxBase:Update()
        if not self.PrimaryPart then
            --warn("not supposed to print", self.Object)
            return self:Remove()
        end

        local color
        if ESP.Highlighted == self.Object then
        color = ESP.HighlightColor
        else
            color = self.Color or self.ColorDynamic and self:ColorDynamic() or ESP:GetColor(self.Object) or ESP.Color
        end

        local allow = true
        if ESP.Overrides.UpdateAllow and not ESP.Overrides.UpdateAllow(self) then
            allow = false
        end
        if self.Player and not ESP.TeamMates and ESP:IsTeamMate(self.Player) then
            allow = false
        end
        if self.Player and not ESP.Players then
            allow = false
        end
        if self.IsEnabled and (type(self.IsEnabled) == "string" and not ESP[self.IsEnabled] or type(self.IsEnabled) == "function" and not self:IsEnabled()) then
            allow = false
        end
        if not workspace:IsAncestorOf(self.PrimaryPart) and not self.RenderInNil then
            allow = false
        end

        if not allow then
            for i,v in pairs(self.Components) do
                v.Visible = false
            end
            return
        end

        if ESP.Highlighted == self.Object then
            color = ESP.HighlightColor
        end

        --calculations--
        local cf = self.PrimaryPart.CFrame
        if ESP.FaceCamera then
            cf = CFrame.new(cf.p, cam.CFrame.p)
        end
        local size = self.Size
        local locs = {
            TopLeft = cf * ESP.BoxShift * CFrame.new(size.X/2,size.Y/2,0),
            TopRight = cf * ESP.BoxShift * CFrame.new(-size.X/2,size.Y/2,0),
            BottomLeft = cf * ESP.BoxShift * CFrame.new(size.X/2,-size.Y/2,0),
            BottomRight = cf * ESP.BoxShift * CFrame.new(-size.X/2,-size.Y/2,0),
            TagPos = cf * ESP.BoxShift * CFrame.new(0,size.Y/2,0),
            Torso = cf * ESP.BoxShift
        }

        if ESP.Boxes then
            local TopLeft, Vis1 = WorldToViewportPoint(cam, locs.TopLeft.p)
            local TopRight, Vis2 = WorldToViewportPoint(cam, locs.TopRight.p)
            local BottomLeft, Vis3 = WorldToViewportPoint(cam, locs.BottomLeft.p)
            local BottomRight, Vis4 = WorldToViewportPoint(cam, locs.BottomRight.p)

            if self.Components.Quad then
                if Vis1 or Vis2 or Vis3 or Vis4 then
                    self.Components.Quad.Visible = true
                    self.Components.Quad.PointA = Vector2.new(TopRight.X, TopRight.Y)
                    self.Components.Quad.PointB = Vector2.new(TopLeft.X, TopLeft.Y)
                    self.Components.Quad.PointC = Vector2.new(BottomLeft.X, BottomLeft.Y)
                    self.Components.Quad.PointD = Vector2.new(BottomRight.X, BottomRight.Y)
                    self.Components.Quad.Color = color
                else
                    self.Components.Quad.Visible = false
                end
            end
        else
            self.Components.Quad.Visible = false
        end

        if ESP.Names then
            local TagPos, Vis5 = WorldToViewportPoint(cam, locs.TagPos.p)
            
            if Vis5 then
                self.Components.Name.Visible = true
                self.Components.Name.Position = Vector2.new(TagPos.X, TagPos.Y)
                self.Components.Name.Text = self.Name
                self.Components.Name.Color = color
                
                self.Components.Distance.Visible = true
                self.Components.Distance.Position = Vector2.new(TagPos.X, TagPos.Y + 14)
                self.Components.Distance.Text = math.floor((cam.CFrame.p - cf.p).magnitude) .."m away"
                self.Components.Distance.Color = color
            else
                self.Components.Name.Visible = false
                self.Components.Distance.Visible = false
            end
        else
            self.Components.Name.Visible = false
            self.Components.Distance.Visible = false
        end
        
        if ESP.Tracers then
            local TorsoPos, Vis6 = WorldToViewportPoint(cam, locs.Torso.p)

            if Vis6 then
                self.Components.Tracer.Visible = true
                self.Components.Tracer.From = Vector2.new(TorsoPos.X, TorsoPos.Y)
                self.Components.Tracer.To = Vector2.new(cam.ViewportSize.X/2,cam.ViewportSize.Y/ESP.AttachShift)
                self.Components.Tracer.Color = color
            else
                self.Components.Tracer.Visible = false
            end
        else
            self.Components.Tracer.Visible = false
        end
    end

    function ESP:Add(obj, options)
        if not obj.Parent and not options.RenderInNil then
            return warn(obj, "has no parent")
        end

        local box = setmetatable({
            Name = options.Name or obj.Name,
            Type = "Box",
            Color = options.Color --[[or self:GetColor(obj)]],
            Size = options.Size or self.BoxSize,
            Object = obj,
            Player = options.Player or plrs:GetPlayerFromCharacter(obj),
            PrimaryPart = options.PrimaryPart or obj.ClassName == "Model" and (obj.PrimaryPart or obj:FindFirstChild("HumanoidRootPart") or obj:FindFirstChildWhichIsA("BasePart")) or obj:IsA("BasePart") and obj,
            Components = {},
            IsEnabled = options.IsEnabled,
            Temporary = options.Temporary,
            ColorDynamic = options.ColorDynamic,
            RenderInNil = options.RenderInNil
        }, boxBase)

        if self:GetBox(obj) then
            self:GetBox(obj):Remove()
        end

        box.Components["Quad"] = Draw("Quad", {
            Thickness = self.Thickness,
            Color = color,
            Transparency = 0,
            Filled = false,
            Visible = self.Disabled and self.Boxes
        })
        box.Components["Name"] = Draw("Text", {
            Text = box.Name,
            Color = box.Color,
            Center = true,
            Outline = true,
            Size = 29,
            Visible = self.Enabled and self.Names
        })
        box.Components["Distance"] = Draw("Text", {
            Color = box.Color,
            Center = true,
            Outline = true,
            Size = 1,
            Visible = self.Enabled and self.Names
        })
        
        box.Components["Tracer"] = Draw("Line", {
            Thickness = ESP.Thickness,
            Color = box.Color,
            Transparency = 1,
            Visible = self.Enabled and self.Tracers
        })
        self.Objects[obj] = box
        
        obj.AncestryChanged:Connect(function(_, parent)
            if parent == nil and ESP.AutoRemove ~= false then
                box:Remove()
            end
        end)
        obj:GetPropertyChangedSignal("Parent"):Connect(function()
            if obj.Parent == nil and ESP.AutoRemove ~= false then
                box:Remove()
            end
        end)

        local hum = obj:FindFirstChildOfClass("Humanoid")
        if hum then
            hum.Died:Connect(function()
                if ESP.AutoRemove ~= false then
                    box:Remove()
                end
            end)
        end

        return box
    end

    local function CharAdded(char)
        local p = plrs:GetPlayerFromCharacter(char)
        if not char:FindFirstChild("HumanoidRootPart") then
            local ev
            ev = char.ChildAdded:Connect(function(c)
                if c.Name == "HumanoidRootPart" then
                    ev:Disconnect()
                    ESP:Add(char, {
                        Name = p.Name,
                        Player = p,
                        PrimaryPart = c
                    })
                end
            end)
        else
            ESP:Add(char, {
                Name = p.Name,
                Player = p,
                PrimaryPart = char.HumanoidRootPart
            })
        end
    end
    local function PlayerAdded(p)
        p.CharacterAdded:Connect(CharAdded)
        if p.Character then
            coroutine.wrap(CharAdded)(p.Character)
        end
    end
    plrs.PlayerAdded:Connect(PlayerAdded)
    for i,v in pairs(plrs:GetPlayers()) do
        if v ~= plr then
            PlayerAdded(v)
        end
    end

    game:GetService("RunService").RenderStepped:Connect(function()
        cam = workspace.CurrentCamera
        for i,v in (ESP.Enabled and pairs or ipairs)(ESP.Objects) do
            if v.Update then
                local s,e = pcall(v.Update, v)
                if not s then warn("[EU]", e, v.Object:GetFullName()) end
            end
        end
    end)

    ----[[ Now Begins WRD's modification for implementation ]]----

    --Sets defaults where required
    if _G.WRDESPEnabled == nil then _G.WRDESPEnabled = true end
    if _G.WRDESPBoxes == nil then _G.WRDESPBoxes = true end
    if _G.WRDESPTeamColors == nil then _G.WRDESPTeamColors = true end
    if _G.WRDESPTracers == nil then _G.WRDESPTracers = false end
    if _G.WRDESPNames == nil then _G.WRDESPNames = true end
	
	--Hacky way to keep up with setting changes
    while wait(.1) do
        ESP:Toggle(_G.WRDESPEnabled or false)
        ESP.Boxes = _G.WRDESPBoxes or false
        ESP.TeamColors = _G.WRDESPTeamColors or false
        ESP.Tracers = _G.WRDESPTracers or false
        ESP.Names = _G.WRDESPNames or false
    end

    _G.WRDESPLoaded = true
end
end)


local dell = Window:NewTab("Money")
local dellSection = dell:NewSection("Money Stuff")

dellSection:NewButton("Cash Aura", "Auto Pick Up Money", function()
    
 game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Cash Aura Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})

local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
	
		while wait() do


local function getMoneyAroundMe() 
    for i, money in ipairs(game.Workspace.Ignored.Drop:GetChildren()) do
        if money.Name == "MoneyDrop" and (money.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 20 then
            fireclickdetector(money.ClickDetector)
        end  
    end
end

 getMoneyAroundMe()
end





end)





dellSection:NewButton("Auto Farm", "cash farm", function()
    game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Auto Farm Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})


local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()


local humanoid = game.Players.LocalPlayer.Character.Humanoid
local tool = game.Players.LocalPlayer.Backpack.Combat

local function getMoneyAroundMe() 
    wait(0.5)
    for i, money in ipairs(game.Workspace.Ignored.Drop:GetChildren()) do
        if money.Name == "MoneyDrop" and (money.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 20 then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = money.CFrame
            fireclickdetector(money.ClickDetector)
            wait(1)
        end  
    end
end




local function startAutoFarm() 
    humanoid:EquipTool(tool)

    for i, v in ipairs(game.Workspace.Cashiers:GetChildren()) do
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Open.CFrame * CFrame.new(0, 0, 2)
        wait(1.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Open.CFrame * CFrame.new(0, 0, 2)

        if v.Open.Size.Z > 1 then
            continue
        end

    

        for i = 0, 15 do
            wait(0.5)
            tool:Activate()
        end

        getMoneyAroundMe()

    end



    wait(0.5)

    humanoid:UnequipTools()
    startAutoFarm()
 
end

startAutoFarm()
end)




local extra = Window:NewTab("Extra")
local extraSection = extra:NewSection("Extras")

MainSection:NewButton("Auto Stomp Z To Toggle", "stomps for u", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Auto Stomp Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    
    
    Toggle = false
 
    while wait(.5) do
        local mouse = game.Players.LocalPlayer:GetMouse()
 
        if Toggle == false then
            game.ReplicatedStorage.MainEvent:FireServer("Stomp")
            mouse.KeyDown:connect(function(k)
             if k == "z" then
                if Toggle == false then 
                   Toggle = true
                    print('Off')
            elseif Toggle == true then 
                    print('On')
                    Toggle = false
                         end
                     end
                 end)
             end
        end
end)


extraSection:NewButton("Q To Teleport", "tp with q", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Q to Tp Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    
    
    plr = game.Players.LocalPlayer

	hum = plr.Character.HumanoidRootPart

	mouse = plr:GetMouse()



	mouse.KeyDown:connect(function(key)

		if key == "q" then

			if mouse.Target then

				hum.CFrame = CFrame.new(mouse.Hit.x, mouse.Hit.y + 5, mouse.Hit.z)

			end

		end
	end)
end)


extraSection:NewButton("Low Graphics", "low gfx", function()
    
 game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Low Gfx Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})


local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()


local decalsyeeted = true -- Leaving this on makes games look shitty but the fps goes up by at least 20.
local g = game
local w = g.Workspace
local l = g.Lighting
local t = w.Terrain
sethiddenproperty(l,"Technology",2)
sethiddenproperty(t,"Decoration",false)
t.WaterWaveSize = 0
t.WaterWaveSpeed = 0
t.WaterReflectance = 0
t.WaterTransparency = 0
l.GlobalShadows = false
l.FogEnd = 9e9
l.Brightness = 0
settings().Rendering.QualityLevel = "Level01"
for i, v in pairs(g:GetDescendants()) do
    if v:IsA("Part") or v:IsA("Union") or v:IsA("CornerWedgePart") or v:IsA("TrussPart") then
        v.Material = "Plastic"
        v.Reflectance = 0
    elseif v:IsA("Decal") or v:IsA("Texture") and decalsyeeted then
        v.Transparency = 1
    elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
        v.Lifetime = NumberRange.new(0)
    elseif v:IsA("Explosion") then
        v.BlastPressure = 1
        v.BlastRadius = 1
    elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
        v.Enabled = false
    elseif v:IsA("MeshPart") then
        v.Material = "Plastic"
        v.Reflectance = 0
        v.TextureID = 10385902758728957
    end
end
for i, e in pairs(l:GetChildren()) do
    if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then
        e.Enabled = false
    end
end
end)



	
		
extraSection:NewButton("Tryhard Animations", "animations for da hood", function()
    
    	 game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "TryHard Animations Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    		
    			local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    				
    				while true do
local Animate = game.Players.LocalPlayer.Character.Animate
Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=782841498"
Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=782841498"
Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616168032"
Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616163682"
Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=1083218792"
Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=1083439238"
Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=707829716"
game.Players.LocalPlayer.Character.Humanoid.Jump = false
wait(1)
end
end)



MainSection:NewButton("Anti Slow", "cant slow down", function()

        game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Anti Slow Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"}) 

local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

loadstring(game:HttpGet("https://pastebin.com/raw/JFrBJBZw"))()
end)



extraSection:NewButton("Fake Macro Hold (V)", "fake macro", function()
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    
    -- the key 2 speed is "Q"
plr = game:GetService('Players').LocalPlayer
down = true
 
function onButton1Down(mouse)
    down = true
    while down do
        if not down then break end
        local char = plr.Character
        char.HumanoidRootPart.Velocity = char.HumanoidRootPart.CFrame.lookVector * 190
        wait()
    end
end
 
function onButton1Up(mouse)
    down = false
end
 
function onSelected(mouse)
    mouse.KeyDown:connect(function(v) if v:lower()=="v"then onButton1Down(mouse)end end)
    mouse.KeyUp:connect(function(v) if v:lower()=="v"then onButton1Up(mouse)end end)
end
onSelected(game.Players.LocalPlayer:GetMouse())
game.StarterGui:SetCore("SendNotification",{
			Title = "Bacon X";
			Text = "Macro Hold (Q)";
			Duration = 5;
		})
end)



TPSection:NewButton("Rifle Gun Teleport", "tp to rifle", function()
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Rifle Teleport Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})


local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-864.332, 2.755, -686.988)
end)

extraSection:NewButton("Animation Pack", "free animations", function()
    
        game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Animation Pack Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
          
                local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
                
                
                -- Animation Pack --












































repeat
    wait()
until game:IsLoaded() and game.Players.LocalPlayer.Character:FindFirstChild("FULLY_LOADED_CHAR") and game.Players.LocalPlayer.PlayerGui.MainScreenGui:FindFirstChild("AnimationPack")

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Lean") then
    game.ReplicatedStorage.ClientAnimations.Lean:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Lay") then
    game.ReplicatedStorage.ClientAnimations.Lay:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Dance1") then
    game.ReplicatedStorage.ClientAnimations.Dance1:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Dance2") then
    game.ReplicatedStorage.ClientAnimations.Dance2:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Greet") then
    game.ReplicatedStorage.ClientAnimations.Greet:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Chest Pump") then
    game.ReplicatedStorage.ClientAnimations["Chest Pump"]:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Praying") then
    game.ReplicatedStorage.ClientAnimations.Praying:Destroy()
end

local Animations = game.ReplicatedStorage.ClientAnimations

local LeanAnimation = Instance.new("Animation", Animations)
LeanAnimation.Name = "Lean"
LeanAnimation.AnimationId = "rbxassetid://3152375249"

local LayAnimation = Instance.new("Animation", Animations)
LayAnimation.Name = "Lay"
LayAnimation.AnimationId = "rbxassetid://3152378852"

local Dance1Animation = Instance.new("Animation", Animations)
Dance1Animation.Name = "Dance1"
Dance1Animation.AnimationId = "rbxassetid://3189773368"

local Dance2Animation = Instance.new("Animation", Animations)
Dance2Animation.Name = "Dance2"
Dance2Animation.AnimationId = "rbxassetid://3189776546"

local GreetAnimation = Instance.new("Animation", Animations)
GreetAnimation.Name = "Greet"
GreetAnimation.AnimationId = "rbxassetid://3189777795"

local ChestPumpAnimation = Instance.new("Animation", Animations)
ChestPumpAnimation.Name = "Chest Pump"
ChestPumpAnimation.AnimationId = "rbxassetid://3189779152"

local PrayingAnimation = Instance.new("Animation", Animations)
PrayingAnimation.Name = "Praying"
PrayingAnimation.AnimationId = "rbxassetid://3487719500"

function AnimationPack(Character)
    Character:WaitForChild'Humanoid'
    repeat
        wait()
    until game.Players.LocalPlayer.Character:FindFirstChild("FULLY_LOADED_CHAR") and game.Players.LocalPlayer.PlayerGui.MainScreenGui:FindFirstChild("AnimationPack")

    local AnimationPack = game:GetService("Players").LocalPlayer.PlayerGui.MainScreenGui.AnimationPack
    local ScrollingFrame = AnimationPack.ScrollingFrame
    local CloseButton = AnimationPack.CloseButton

    local Lean = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(LeanAnimation)

    local Lay = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(LayAnimation)

    local Dance1 = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(Dance1Animation)

    local Dance2 = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(Dance2Animation)

    local Greet = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(GreetAnimation)

    local ChestPump = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(ChestPumpAnimation)

    local Praying = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(PrayingAnimation)

    AnimationPack.Visible = true

    AnimationPack.ScrollingFrame.UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Lean" then
                v.Name = "LeanButton"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Lay" then
                v.Name = "LayButton"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Dance1" then
                v.Name = "Dance1Button"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Dance2" then
                v.Name = "Dance2Button"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Greet" then
                v.Name = "GreetButton"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Chest Pump" then
                v.Name = "ChestPumpButton"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Praying" then
                v.Name = "PrayingButton"
            end
        end
    end

    function Stop()
        Lean:Stop()
        Lay:Stop()
        Dance1:Stop()
        Dance2:Stop()
        Greet:Stop()
        ChestPump:Stop()
        Praying:Stop()
    end

    local LeanTextButton = ScrollingFrame.LeanButton
    local LayTextButton = ScrollingFrame.LayButton
    local Dance1TextButton = ScrollingFrame.Dance1Button
    local Dance2TextButton = ScrollingFrame.Dance2Button
    local GreetTextButton = ScrollingFrame.GreetButton
    local ChestPumpTextButton = ScrollingFrame.ChestPumpButton
    local PrayingTextButton = ScrollingFrame.PrayingButton

    AnimationPack.MouseButton1Click:Connect(function()
        if ScrollingFrame.Visible == false then
            ScrollingFrame.Visible = true
            CloseButton.Visible = true
        end
    end)
    CloseButton.MouseButton1Click:Connect(function()
        if ScrollingFrame.Visible == true then
            ScrollingFrame.Visible = false
            CloseButton.Visible = false
        end
    end)
    LeanTextButton.MouseButton1Click:Connect(function()
        Stop()
        Lean:Play()
    end)
    LayTextButton.MouseButton1Click:Connect(function()
        Stop()
        Lay:Play()
    end)
    Dance1TextButton.MouseButton1Click:Connect(function()
        Stop()
        Dance1:Play()
    end)
    Dance2TextButton.MouseButton1Click:Connect(function()
        Stop()
        Dance2:Play()
    end)
    GreetTextButton.MouseButton1Click:Connect(function()
        Stop()
        Greet:Play()
    end)
    ChestPumpTextButton.MouseButton1Click:Connect(function()
        Stop()
        ChestPump:Play()
    end)
    PrayingTextButton.MouseButton1Click:Connect(function()
        Stop()
        Praying:Play()
    end)

    game:GetService("Players").LocalPlayer.Character.Humanoid.Running:Connect(function()
        Stop()
    end)

    game:GetService("Players").LocalPlayer.CharacterAdded:Connect(function()
        Stop()
    end)
end
AnimationPack(game.Players.LocalPlayer.Character)
game.Players.LocalPlayer.CharacterAdded:Connect(AnimationPack)
end)



MainSection:NewButton("Anti Bag", "cant get baged me irl foril", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Anti Bag Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    
    local LP = game.Players.LocalPlayer;

    for i,v in ipairs(LP.Character:GetDescendants()) do
        if v.Name == "Christmas_Sock" then v:Destroy()
            end
        end
            
        LP.Character.ChildAdded:Connect(function()
        wait(0.3)
        for i,v in ipairs(LP.Character:GetDescendants()) do
        if v.Name == "Christmas_Sock" then v:Destroy()
        end
        end
        end)
end)




monkeySection:NewButton("God Mode", "gives god mode", function()
     
      game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "God Mode Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
     
     
     local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
     
     local localPlayer = game:GetService('Players').LocalPlayer;
                local localCharacter = localPlayer.Character;
                localCharacter:FindFirstChildOfClass('Humanoid').Health = 0;
                local newCharacter = localPlayer.CharacterAdded:Wait();
                local spoofFolder = Instance.new('Folder');
                spoofFolder.Name = 'FULLY_LOADED_CHAR';
                spoofFolder.Parent = newCharacter;
                newCharacter:WaitForChild('RagdollConstraints'):Destroy();
                local spoofValue = Instance.new('BoolValue', newCharacter);
                spoofValue.Name = 'RagdollConstraints';
                local name = game.Players.LocalPlayer.Name
                local lol =    game.Workspace:WaitForChild(name)
                local money = Instance.new("Folder",game.Players.LocalPlayer.Character);money.Name = "FULLY_LOADED_CHAR"
                lol.Parent = game.Workspace.Players
                game.Players.LocalPlayer.Character:WaitForChild("BodyEffects")
                game.Players.LocalPlayer.Character.BodyEffects.BreakingParts:Destroy()
end)




extraSection:NewButton("No Jump Cooldown", "infinite jump", function()
    
         game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "No Jump Cooldown Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
        
        
        
        local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
        
        --auto exc support
if not game.IsLoaded(game) then 
    game.Loaded.Wait(game.Loaded);
end

-- variables 
local IsA = game.IsA;
local newindex = nil 

-- main hook
newindex = hookmetamethod(game, "__newindex", function(self, Index, Value)
    if not checkcaller() and IsA(self, "Humanoid") and Index == "JumpPower" then 
        return
    end
    
    return newindex(self, Index, Value);
end)
end)





scriptwareSection:NewButton("Auto Reload", "reloads for u", function()
        
         game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Auto Reload Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
        
        local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
        
        
        _G.AutoReload = true -- change to false if u don't want it anymore.

while _G.AutoReload == true and game:GetService("RunService").Heartbeat:Wait() do
if game:GetService("Players").LocalPlayer.Character:FindFirstChildWhichIsA("Tool") then
            if game:GetService("Players").LocalPlayer.Character:FindFirstChildWhichIsA("Tool"):FindFirstChild("Ammo") then
                if game:GetService("Players").LocalPlayer.Character:FindFirstChildWhichIsA("Tool"):FindFirstChild("Ammo").Value <= 0 then
                    game:GetService("ReplicatedStorage").MainEvent:FireServer("Reload", game:GetService("Players").LocalPlayer.Character:FindFirstChildWhichIsA("Tool")) 
                    wait(1)
                end
            end
        end
end
end)





HumanSection:NewButton("Chat Spy", "spys on chat", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Chat Spy Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    

local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

repeat wait() until game:GetService("ContentProvider").RequestQueueSize == 0;
repeat wait() until game:IsLoaded();

-- // Vars
local Players = game:GetService("Players");
local StarterGui = game:GetService("StarterGui");
local ReplicatedStorage = game:GetService("ReplicatedStorage");
local LocalPlayer = Players.LocalPlayer;
local PlayerGui = LocalPlayer:WaitForChild("PlayerGui");
local DefaultChatSystemChatEvents = ReplicatedStorage:WaitForChild("DefaultChatSystemChatEvents");
local SayMessageRequest = DefaultChatSystemChatEvents:WaitForChild("SayMessageRequest");
local OnMessageDoneFiltering = DefaultChatSystemChatEvents:WaitForChild("OnMessageDoneFiltering");
getgenv().ChatSpy = {
    Enabled = true,
    SpyOnSelf = false,
    Public = false,
    Chat = {
        Colour  = Color3.fromRGB(255, 0, 0),
        Font = Enum.Font.SourceSans,
        TextSize = 18,
        Text = "",
    },
    IgnoreList = {
        {Message = ":part/1/1/1", ExactMatch = true},
        {Message = ":part/10/10/10", ExactMatch = true},
        {Message = "A?????????", ExactMatch = false},
        {Message = ":colorshifttop 10000 0 0", ExactMatch = true},
        {Message = ":colorshiftbottom 10000 0 0", ExactMatch = true},
        {Message = ":colorshifttop 0 10000 0", ExactMatch = true},
        {Message = ":colorshiftbottom 0 10000 0", ExactMatch = true},
        {Message = ":colorshifttop 0 0 10000", ExactMatch = true},
        {Message = ":colorshiftbottom 0 0 10000", ExactMatch = true},
    },
};

-- // Function
function ChatSpy.checkIgnored(message)
    for i = 1, #ChatSpy.IgnoreList do
        local v = ChatSpy.IgnoreList[i];
        if (v.ExactMatch and message == v.Message) or (not v.ExactMatch and string.match(v.Message, message)) then 
            return true;
        end;
    end;
    return false;
end;

function ChatSpy.onChatted(targetPlayer, message)
    if (targetPlayer == LocalPlayer and string.lower(message):sub(1, 4) == "/spy") then
        ChatSpy.Enabled = not ChatSpy.Enabled; wait(0.3);
        ChatSpy.Chat.Text = "[SPY] - "..(ChatSpy.Enabled and "Enabled." or "Disabled.");

        StarterGui:SetCore("ChatMakeSystemMessage", ChatSpy.Chat);
    elseif (ChatSpy.Enabled and (ChatSpy.SpyOnSelf or targetPlayer ~= LocalPlayer)) then
        local message = message:gsub("[\n\r]",''):gsub("\t",' '):gsub("[ ]+",' ');

        local Hidden = true;
        local Connection = OnMessageDoneFiltering.OnClientEvent:Connect(function(packet, channel)
            if (packet.SpeakerUserId == targetPlayer.UserId and packet.Message == message:sub(#message - #packet.Message + 1) and (channel == "All" or (channel == "Team" and not ChatSpy.Public and Players[packet.FromSpeaker].Team == LocalPlayer.Team))) then
                Hidden = false;
            end;
        end);

        wait(1);
        Connection:Disconnect();

        if (Hidden and ChatSpy.Enabled and not ChatSpy.checkIgnored(message)) then
            if (#message > 1200) then
                message = message:sub(1200) .. "...";
            end;
            ChatSpy.Chat.Text = "[SPY] - ["..targetPlayer.Name.."]: " .. message;
            if (ChatSpy.Public) then SayMessageRequest:FireServer(ChatSpy.Chat.Text, "All"); else StarterGui:SetCore("ChatMakeSystemMessage", ChatSpy.Chat); end;
        end;
    end;
end;

-- // Handling Chats
local AllPlayers = Players:GetPlayers();
for i = 1, #AllPlayers do
    local player = AllPlayers[i];
    player.Chatted:Connect(function(message)
        ChatSpy.onChatted(player, message);
    end);
end;

Players.PlayerAdded:Connect(function(player)
    player.Chatted:Connect(function(message)
        ChatSpy.onChatted(player, message);
    end);
end);

-- // Initialise Text
ChatSpy.Chat.Text = "[SPY] - "..(ChatSpy.Enabled and "Enabled." or "Disabled.");
StarterGui:SetCore("ChatMakeSystemMessage", ChatSpy.Chat);

-- // Update Chat Frame
local chatFrame = LocalPlayer.PlayerGui.Chat.Frame;
chatFrame.ChatChannelParentFrame.Visible = true;
chatFrame.ChatBarParentFrame.Position = chatFrame.ChatChannelParentFrame.Position + UDim2.new(UDim.new(), chatFrame.ChatChannelParentFrame.Size.Y);
end)




HumanSection:NewButton("Rainbow Body", "turns u rgb", function()
   
    	 game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Rainbow Body Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    	 	
    	 	 	 
    	 	 	 	local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
    	 	 	 		
    	 	 	 			for i, v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
			if v:IsA("MeshPart") then
				v.Material = "ForceField"
				spawn(function()
					while wait() do
						for i, v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
							if v:IsA("MeshPart") then
								v.Color = Color3.fromHSV(tick()%5/5,1,1)
								wait()
							end
						end 
					end
				end)
			end
		end
end)




MainSection:NewButton("Teleport To Player", "teleport to anyplayer", function()
    
 game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Teleport To Player Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})

local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

local lp = game:FindService("Players").LocalPlayer
 
local function gplr(String)
	local Found = {}
	local strl = String:lower()
	if strl == "all" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			table.insert(Found,v)
		end
	elseif strl == "others" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name ~= lp.Name then
				table.insert(Found,v)
			end
		end 
	elseif strl == "me" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name == lp.Name then
				table.insert(Found,v)
			end
		end 
	else
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name:lower():sub(1, #String) == String:lower() then
				table.insert(Found,v)
			end
		end 
	end
	return Found 
end

local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
local TextBox = Instance.new("TextBox")
local Drop_Shadow = Instance.new("ImageLabel")
local Drop_Shadow_2 = Instance.new("ImageLabel")
local TextLabel = Instance.new("TextLabel")
local TextButton = Instance.new("TextButton")
local UICorner_2 = Instance.new("UICorner")
local TextButton_2 = Instance.new("TextButton")
local UICorner_3 = Instance.new("UICorner")



ScreenGui.Parent = game.CoreGui

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(32, 32, 32)
Frame.BorderColor3 = Color3.fromRGB(32, 32, 32)
Frame.Position = UDim2.new(0.312854379, 0, 0.0988024324, 0)
Frame.Size = UDim2.new(0, 260, 0, 282)
Frame.Active = true
Frame.Draggable = true

UICorner.CornerRadius = UDim.new(0, 5)
UICorner.Parent = Frame

TextBox.Parent = Frame
TextBox.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
TextBox.BorderColor3 = Color3.fromRGB(50, 50, 50)
TextBox.Position = UDim2.new(0.115384616, 0, 0.191489369, 0)
TextBox.Size = UDim2.new(0, 200, 0, 50)
TextBox.Font = Enum.Font.SourceSans
TextBox.Text = "Player Name Here"
TextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
TextBox.TextSize = 14.000

Drop_Shadow.Name = "Drop_Shadow"
Drop_Shadow.Parent = Frame
Drop_Shadow.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Drop_Shadow.BackgroundTransparency = 1.000
Drop_Shadow.Position = UDim2.new(0, -46, 0, -41)
Drop_Shadow.Size = UDim2.new(1.33725142, 1, 1.3021301, 1)
Drop_Shadow.ZIndex = -5
Drop_Shadow.Image = "rbxassetid://1113384364"
Drop_Shadow.ImageTransparency = 0.200
Drop_Shadow.ScaleType = Enum.ScaleType.Slice
Drop_Shadow.SliceCenter = Rect.new(50, 50, 50, 50)

Drop_Shadow_2.Name = "Drop_Shadow"
Drop_Shadow_2.Parent = Frame
Drop_Shadow_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Drop_Shadow_2.BackgroundTransparency = 1.000
Drop_Shadow_2.Position = UDim2.new(0, -46, 0, -41)
Drop_Shadow_2.Size = UDim2.new(1.33725142, 1, 1.3021301, 1)
Drop_Shadow_2.ZIndex = -5
Drop_Shadow_2.Image = "rbxassetid://1113384364"
Drop_Shadow_2.ImageTransparency = 0.200
Drop_Shadow_2.ScaleType = Enum.ScaleType.Slice
Drop_Shadow_2.SliceCenter = Rect.new(50, 50, 50, 50)

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.Size = UDim2.new(0, 260, 0, 50)
TextLabel.Font = Enum.Font.Arial
TextLabel.Text = "Bacon x"
TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.TextScaled = true
TextLabel.TextSize = 14.000
TextLabel.TextWrapped = true

TextButton.Parent = Frame
TextButton.BackgroundColor3 = Color3.fromRGB(43, 43, 43)
TextButton.Position = UDim2.new(0.115384616, 0, 0.489361703, 0)
TextButton.Size = UDim2.new(0, 200, 0, 50)
TextButton.Font = Enum.Font.Fantasy
TextButton.Text = "Tp To Player"
TextButton.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton.TextSize = 17.000
TextButton.MouseButton1Down:connect(function()
	local lplayer = game:GetService('Players').LocalPlayer

	local yeeting = false
	function GetPlayer(String)
		local Found = {}
		local strl = String:lower()
		if strl == "all" then
			for i,v in pairs(game:GetService("Players"):GetPlayers()) do
				table.insert(Found,v)
			end
		elseif strl == "Random" then
			for i,v in pairs(game:GetService("Players"):GetPlayers()) do
				if v.Name ~= lplayer.Name then
					table.insert(Found,v)
				end
			end 
		elseif strl == "me" then
			for i,v in pairs(game:GetService("Players"):GetPlayers()) do
				if v.Name == lplayer.Name then
					table.insert(Found,v)
				end
			end 
		else
			for i,v in pairs(game:GetService("Players"):GetPlayers()) do
				if v.Name:lower():sub(1, #String) == String:lower() then
					table.insert(Found,v)
				end
			end 
		end
		return Found 
	end
	function ahh(thing)
		local asd = {'yeet','gui','yeet gui'}
		local f = string.upper(asd[math.random(1,#asd)])
		return f
	end

	local target = unpack(GetPlayer(TextBox.Text)).Character

	game:GetService'Players'.LocalPlayer.Character.HumanoidRootPart.CFrame = target.Head.CFrame;coin.Location = target.Head.Position game["Run Service"].Heartbeat:wait()

end)

UICorner_2.Parent = TextButton

TextButton_2.Parent = Frame
TextButton_2.BackgroundColor3 = Color3.fromRGB(43, 43, 43)
TextButton_2.Position = UDim2.new(0.115384616, 0, 0.741134763, 0)
TextButton_2.Size = UDim2.new(0, 200, 0, 50)
TextButton_2.Font = Enum.Font.Arial
TextButton_2.Text = "Fling Player"
TextButton_2.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton_2.TextSize = 15.000
TextButton_2.MouseButton1Down:connect(function()
	local Target = gplr(TextBox.Text)
	if Target[1] then
		Target = Target[1]

		local Thrust = Instance.new('BodyThrust', lp.Character.HumanoidRootPart)
		Thrust.Force = Vector3.new(9999,9999,9999)
		Thrust.Name = "YeetForce"
		repeat
			lp.Character.HumanoidRootPart.CFrame = Target.Character.HumanoidRootPart.CFrame
			Thrust.Location = Target.Character.HumanoidRootPart.Position
			game:FindService("RunService").Heartbeat:wait()
		until not Target.Character:FindFirstChild("Head")
	else
		
	end
end)

UICorner_3.Parent = TextButton_2


    
end)


extraSection:NewButton("Use All Tools", "take out all tools", function()
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Use All Tools Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    	while true do

local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

game.Players.LocalPlayer.Backpack:FindFirstChildOfClass("Tool").Parent = game.Players.LocalPlayer.Character
end
wait(120)
end)

scriptwareSection:NewButton("Lock (Q)", "aimlock", function()
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Aimlock (Q) Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
     
      
       
        local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
         
           getgenv().AimPart = "HumanoidRootPart"
        getgenv().AimlockKey = "q"
        getgenv().AimRadius = 30
        getgenv().ThirdPerson = true
        getgenv().FirstPerson = true
        getgenv().TeamCheck = false
        getgenv().PredictMovement = true
        getgenv().PredictionVelocity = 6
        local L_27_, L_28_, L_29_, L_30_ =
                game:GetService "Players",
                game:GetService "UserInputService",
                game:GetService "RunService",
                game:GetService "StarterGui"
        local L_31_, L_32_, L_33_, L_34_, L_35_, L_36_, L_37_ =
                L_27_.LocalPlayer,
                L_27_.LocalPlayer:GetMouse(),
                workspace.CurrentCamera,
                CFrame.new,
                Ray.new,
                Vector3.new,
                Vector2.new
        local L_38_, L_39_, L_40_ = true, false, false
        local L_41_
        getgenv().CiazwareUniversalAimbotLoaded = true
        getgenv().WorldToViewportPoint = function(L_42_arg0)
            return L_33_:WorldToViewportPoint(L_42_arg0)
        end
        getgenv().WorldToScreenPoint = function(L_43_arg0)
            return L_33_.WorldToScreenPoint(L_33_, L_43_arg0)
        end
        getgenv().GetObscuringObjects = function(L_44_arg0)
            if L_44_arg0 and L_44_arg0:FindFirstChild(getgenv().AimPart) and L_31_ and L_31_.Character:FindFirstChild("Head") then
                local L_45_ = workspace:FindPartOnRay(L_35_(L_44_arg0[getgenv().AimPart].Position, L_31_.Character.Head.Position))
                if L_45_ then
                    return L_45_:IsDescendantOf(L_44_arg0)
                end
            end
        end
        getgenv().GetNearestTarget = function()
            local L_46_ = {}
            local L_47_ = {}
            local L_48_ = {}
            for L_50_forvar0, L_51_forvar1 in pairs(L_27_:GetPlayers()) do
                if L_51_forvar1 ~= L_31_ then
                    table.insert(L_46_, L_51_forvar1)
                end
            end
            for L_52_forvar0, L_53_forvar1 in pairs(L_46_) do
                if L_53_forvar1.Character ~= nil then
                    local L_54_ = L_53_forvar1.Character:FindFirstChild("Head")
                    if getgenv().TeamCheck == true and L_53_forvar1.Team ~= L_31_.Team then
                        local L_55_ =
                                (L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
                        local L_56_ =
                                Ray.new(
                                game.Workspace.CurrentCamera.CFrame.p,
                                (L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_55_
                            )
                        local L_57_, L_58_ = game.Workspace:FindPartOnRay(L_56_, game.Workspace)
                        local L_59_ = math.floor((L_58_ - L_54_.Position).magnitude)
                        L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_55_
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_59_
                        table.insert(L_48_, L_59_)
                    elseif getgenv().TeamCheck == false and L_53_forvar1.Team == L_31_.Team then
                        local L_60_ =
                                (L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
                        local L_61_ =
                                Ray.new(
                                game.Workspace.CurrentCamera.CFrame.p,
                                (L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_60_
                            )
                        local L_62_, L_63_ = game.Workspace:FindPartOnRay(L_61_, game.Workspace)
                        local L_64_ = math.floor((L_63_ - L_54_.Position).magnitude)
                        L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_60_
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_64_
                        table.insert(L_48_, L_64_)
                    end
                end
            end
            if unpack(L_48_) == nil then
                return nil
            end
            local L_49_ = math.floor(math.min(unpack(L_48_)))
            if L_49_ > getgenv().AimRadius then
                return nil
            end
            for L_65_forvar0, L_66_forvar1 in pairs(L_47_) do
                if L_66_forvar1.diff == L_49_ then
                    return L_66_forvar1.plr
                end
            end
            return nil
        end
        L_32_.KeyDown:Connect(
                function(L_67_arg0)
            if L_67_arg0 == AimlockKey and L_41_ == nil then
                pcall(
                            function()
                    if L_39_ ~= true then
                        L_39_ = true
                    end
                    local L_68_
                    L_68_ = GetNearestTarget()
                    if L_68_ ~= nil then
                        L_41_ = L_68_
                    end
                end
                        )
            elseif L_67_arg0 == AimlockKey and L_41_ ~= nil then
                if L_41_ ~= nil then
                    L_41_ = nil
                end
                if L_39_ ~= false then
                    L_39_ = false
                end
            end
        end
            )
        L_29_.RenderStepped:Connect(
                function()
            if getgenv().ThirdPerson == true and getgenv().FirstPerson == true then
                if
                            (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 or
                                (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1
                         then
                    L_40_ = true
                else
                    L_40_ = false
                end
            elseif getgenv().ThirdPerson == true and getgenv().FirstPerson == false then
                if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 then
                    L_40_ = true
                else
                    L_40_ = false
                end
            elseif getgenv().ThirdPerson == false and getgenv().FirstPerson == true then
                if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1 then
                    L_40_ = true
                else
                    L_40_ = false
                end
            end
            if L_38_ == true and L_39_ == true then
                if L_41_ and L_41_.Character and L_41_.Character:FindFirstChild(getgenv().AimPart) then
                    if getgenv().FirstPerson == true then
                        if L_40_ == true then
                            if getgenv().PredictMovement == true then
                                L_33_.CFrame =
                                            L_34_(
                                            L_33_.CFrame.p,
                                            L_41_.Character[getgenv().AimPart].Position +
                                                L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
                                        )
                            elseif getgenv().PredictMovement == false then
                                L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
                            end
                        end
                    elseif getgenv().ThirdPerson == true then
                        if L_40_ == true then
                            if getgenv().PredictMovement == true then
                                L_33_.CFrame =
                                            L_34_(
                                            L_33_.CFrame.p,
                                            L_41_.Character[getgenv().AimPart].Position +
                                                L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
                                        )
                            elseif getgenv().PredictMovement == false then
                                L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
                            end
                        end
                    end
                end
            end
        end
            )
end)

scriptwareSection:NewButton("Lock (E)", "aimlock", function()
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Aimlock (E) Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
      
      
      local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
      
      getgenv().AimPart = "HumanoidRootPart"
        getgenv().AimlockKey = "e"
        getgenv().AimRadius = 30
        getgenv().ThirdPerson = true
        getgenv().FirstPerson = true
        getgenv().TeamCheck = false
        getgenv().PredictMovement = true
        getgenv().PredictionVelocity = 6
        local L_27_, L_28_, L_29_, L_30_ =
                game:GetService "Players",
                game:GetService "UserInputService",
                game:GetService "RunService",
                game:GetService "StarterGui"
        local L_31_, L_32_, L_33_, L_34_, L_35_, L_36_, L_37_ =
                L_27_.LocalPlayer,
                L_27_.LocalPlayer:GetMouse(),
                workspace.CurrentCamera,
                CFrame.new,
                Ray.new,
                Vector3.new,
                Vector2.new
        local L_38_, L_39_, L_40_ = true, false, false
        local L_41_
        getgenv().CiazwareUniversalAimbotLoaded = true
        getgenv().WorldToViewportPoint = function(L_42_arg0)
            return L_33_:WorldToViewportPoint(L_42_arg0)
        end
        getgenv().WorldToScreenPoint = function(L_43_arg0)
            return L_33_.WorldToScreenPoint(L_33_, L_43_arg0)
        end
        getgenv().GetObscuringObjects = function(L_44_arg0)
            if L_44_arg0 and L_44_arg0:FindFirstChild(getgenv().AimPart) and L_31_ and L_31_.Character:FindFirstChild("Head") then
                local L_45_ = workspace:FindPartOnRay(L_35_(L_44_arg0[getgenv().AimPart].Position, L_31_.Character.Head.Position))
                if L_45_ then
                    return L_45_:IsDescendantOf(L_44_arg0)
                end
            end
        end
        getgenv().GetNearestTarget = function()
            local L_46_ = {}
            local L_47_ = {}
            local L_48_ = {}
            for L_50_forvar0, L_51_forvar1 in pairs(L_27_:GetPlayers()) do
                if L_51_forvar1 ~= L_31_ then
                    table.insert(L_46_, L_51_forvar1)
                end
            end
            for L_52_forvar0, L_53_forvar1 in pairs(L_46_) do
                if L_53_forvar1.Character ~= nil then
                    local L_54_ = L_53_forvar1.Character:FindFirstChild("Head")
                    if getgenv().TeamCheck == true and L_53_forvar1.Team ~= L_31_.Team then
                        local L_55_ =
                                (L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
                        local L_56_ =
                                Ray.new(
                                game.Workspace.CurrentCamera.CFrame.p,
                                (L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_55_
                            )
                        local L_57_, L_58_ = game.Workspace:FindPartOnRay(L_56_, game.Workspace)
                        local L_59_ = math.floor((L_58_ - L_54_.Position).magnitude)
                        L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_55_
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_59_
                        table.insert(L_48_, L_59_)
                    elseif getgenv().TeamCheck == false and L_53_forvar1.Team == L_31_.Team then
                        local L_60_ =
                                (L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
                        local L_61_ =
                                Ray.new(
                                game.Workspace.CurrentCamera.CFrame.p,
                                (L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_60_
                            )
                        local L_62_, L_63_ = game.Workspace:FindPartOnRay(L_61_, game.Workspace)
                        local L_64_ = math.floor((L_63_ - L_54_.Position).magnitude)
                        L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_60_
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
                        L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_64_
                        table.insert(L_48_, L_64_)
                    end
                end
            end
            if unpack(L_48_) == nil then
                return nil
            end
            local L_49_ = math.floor(math.min(unpack(L_48_)))
            if L_49_ > getgenv().AimRadius then
                return nil
            end
            for L_65_forvar0, L_66_forvar1 in pairs(L_47_) do
                if L_66_forvar1.diff == L_49_ then
                    return L_66_forvar1.plr
                end
            end
            return nil
        end
        L_32_.KeyDown:Connect(
                function(L_67_arg0)
            if L_67_arg0 == AimlockKey and L_41_ == nil then
                pcall(
                            function()
                    if L_39_ ~= true then
                        L_39_ = true
                    end
                    local L_68_
                    L_68_ = GetNearestTarget()
                    if L_68_ ~= nil then
                        L_41_ = L_68_
                    end
                end
                        )
            elseif L_67_arg0 == AimlockKey and L_41_ ~= nil then
                if L_41_ ~= nil then
                    L_41_ = nil
                end
                if L_39_ ~= false then
                    L_39_ = false
                end
            end
        end
            )
        L_29_.RenderStepped:Connect(
                function()
            if getgenv().ThirdPerson == true and getgenv().FirstPerson == true then
                if
                            (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 or
                                (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1
                         then
                    L_40_ = true
                else
                    L_40_ = false
                end
            elseif getgenv().ThirdPerson == true and getgenv().FirstPerson == false then
                if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 then
                    L_40_ = true
                else
                    L_40_ = false
                end
            elseif getgenv().ThirdPerson == false and getgenv().FirstPerson == true then
                if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1 then
                    L_40_ = true
                else
                    L_40_ = false
                end
            end
            if L_38_ == true and L_39_ == true then
                if L_41_ and L_41_.Character and L_41_.Character:FindFirstChild(getgenv().AimPart) then
                    if getgenv().FirstPerson == true then
                        if L_40_ == true then
                            if getgenv().PredictMovement == true then
                                L_33_.CFrame =
                                            L_34_(
                                            L_33_.CFrame.p,
                                            L_41_.Character[getgenv().AimPart].Position +
                                                L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
                                        )
                            elseif getgenv().PredictMovement == false then
                                L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
                            end
                        end
                    elseif getgenv().ThirdPerson == true then
                        if L_40_ == true then
                            if getgenv().PredictMovement == true then
                                L_33_.CFrame =
                                            L_34_(
                                            L_33_.CFrame.p,
                                            L_41_.Character[getgenv().AimPart].Position +
                                                L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
                                        )
                            elseif getgenv().PredictMovement == false then
                                L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
                            end
                        end
                    end
                end
            end
        end
            )
end)










HumanSection:NewButton("Walk On Walls", "Spider Man", function()
    


 game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Walk On Walls Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})



loadstring(game:HttpGet("https://raw.githubusercontent.com/dylannpro123/enclosed/main/resources/wow", true))()


    
end)




HumanSection:NewButton("Back Flip", "flip", function()
	
	game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Back Flip Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})

       
        local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
        
        local Player = game.Players.LocalPlayer
		local niggers = Player.Character:FindFirstChildWhichIsA("Humanoid"):LoadAnimation(game.ReplicatedStorage.ClientAnimations.Roll)
		niggers:Play()

end)



HumanSection:NewButton("AirStrike Gun", "Floats Gun", function()
	
	game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Back Flip Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})

       local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
       	
       		for _, v in pairs(game:GetService("Players").LocalPlayer.Character:GetChildren()) do
            if v:isA("Tool") then
                v.GripPos = Vector3.new(10,-10,10)
            end
        end
    
       
end)



dellSection:NewButton("Cash ESP", "cash farm", function()
	game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Cash ESP Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
	
	local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
        
        local ESPholder = Instance.new("Folder", game.CoreGui)
		function cham(object)
			if object.Name == "MoneyDrop" then
				local a = Instance.new("BoxHandleAdornment", ESPholder)
				a.Adornee = object
				a.AlwaysOnTop = true
				a.ZIndex = 10
				a.Size = object.Size
				a.Transparency = 0.3
				a.Color = object.BrickColor
				local bill = object:WaitForChild("BillboardGui")
				bill.AlwaysOnTop = true
				bill.Size = UDim2.new(2, 10, 1, 5)
				spawn(function()
					while true do
						if object.Parent.ChildRemoving:wait() == object then
							a:Destroy()
							break
						end
					end
				end)
			end
		end
		for i, v in next, game.Workspace.Ignored.Drop:GetChildren() do
			cham(v)
		end
		game.Workspace.Ignored.Drop.ChildAdded:connect(cham)
	
end)




dellSection:NewButton("Cash Bring", "cash farm", function()
game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Cash Bring Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
	
	local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

for e, v in pairs(game.Workspace.Ignored.Drop:GetChildren()) do
            if v.Name == "MoneyDrop" then
                v.Position = game.Players.LocalPlayer.Character.Head.CFrame.p + Vector3.new(0, 1, 0)
                v.Anchored = false
            end
        end
 

end)


local test = Window:NewTab("Auto Farm")
local testSection = test:NewSection("Auto Farm's")


testSection:NewButton("Letuce Farm", "auto skinny", function()
game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Auto Skinny Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
	
	local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

local player = game.Players.LocalPlayer
		local playerposit = CFrame.new(-84.2903137, 25.4502373, -632.315063, 0.0326573513, 6.83068393e-08, -0.999466658, 7.3860158e-09, 1, 6.85846331e-08, 0.999466658, -9.62186775e-09, 0.0326573513)
		if not game.Players.LocalPlayer.Character:FindFirstChild("[Lettuce]") then
			player.Character.HumanoidRootPart.CFrame = playerposit
			local ClickClick = game:GetService("Workspace").Ignored.Shop["[Lettuce] - $5"]:FindFirstChild("ClickDetector")
			for i = 1, 200 do
				wait(0.9)
				fireclickdetector(ClickClick)
				wait(0.4)
				game.Players.LocalPlayer.Backpack:FindFirstChild("[Lettuce]").Parent = player.Character
				wait(0.5)
				game:GetService("Players").LocalPlayer.Character["[Lettuce]"]:Activate()
			end
		end

end)

HumanSection:NewButton("Admin Fly", "Mod Fly", function()
	game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Admin Fly Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
	
	local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

       -- // Services
local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- // Vars
local tablefind = table.find
local MainEvent = ReplicatedStorage.MainEvent
local SpoofTable = {
    WalkSpeed = 16,
    JumpPower = 50
}

-- // Configuration
local Flags = {
    "CHECKER_1",
    "TeleportDetect",
    "OneMoreTime"
}

-- // __namecall hook
local __namecall
__namecall = hookmetamethod(game, "__namecall", function(...)
    -- // Vars
    local args = {...}
    local self = args[1]
    local method = getnamecallmethod()
    local caller = getcallingscript()

    -- // See if the game is trying to alert the server
    if (method == "FireServer" and self == MainEvent and tablefind(Flags, args[2])) then
        return
    end

    -- // Anti Crash
    if (not checkcaller() and getfenv(2).crash) then
        -- // Hook the crash function to make it not work
        hookfunction(getfenv(2).crash, function()
            warn("Crash Attempt") 
        end)
    end
    
    -- //
    return __namecall(...)
end)

-- // __index hook
local __index
__index = hookmetamethod(game, "__index", function(t, k)
    -- // Make sure it's trying to get our humanoid's ws/jp
    if (not checkcaller() and t:IsA("Humanoid") and (k == "WalkSpeed" or k == "JumpPower")) then
        -- // Return spoof values
        return SpoofTable[k]
    end

    -- //
    return __index(t, k)
end)

-- // __newindex hook
local __newindex
__newindex = hookmetamethod(game, "__newindex", function(t, k, v)
    -- // Make sure it's trying to set our humanoid's ws/jp
    if (not checkcaller() and t:IsA("Humanoid") and (k == "WalkSpeed" or k == "JumpPower")) then
        -- // Add values to spoof table
        SpoofTable[k] = v

        -- // Disallow the set
        return
    end
    
    -- //
    return __newindex(t, k, v)
end)
        	
        	 	
        	 	 	
        	 	 	 	
        	 	 	 	 	
        	 	 	 	 	 	
         function Fly()
            function sandbox(var,func)
                local env = getfenv(func)
                local newenv = setmetatable({},{
                    __index = function(self,k)
                        if k=="script" then
                            return var
                        else
                            return env[k]
                        end
                    end,
                })
                setfenv(func,newenv)
                return func
            end
            cors = {}
            mas = Instance.new("Model",game:GetService("Lighting"))
            Tool0 = Instance.new("Tool")
            LocalScript1 = Instance.new("LocalScript")
            Sound2 = Instance.new("Sound")
            Sound3 = Instance.new("Sound")
            Animation4 = Instance.new("Animation")
            RemoteEvent5 = Instance.new("RemoteEvent")
            Animation6 = Instance.new("Animation")
            Tool0.Name = "Fly"
            Tool0.Parent = mas
            Tool0.CanBeDropped = false
            Tool0.RequiresHandle = false
            LocalScript1.Name = "local"
            LocalScript1.Parent = Tool0
            table.insert(cors,sandbox(LocalScript1,function()
                wait();
                local l__LocalPlayer__1 = game.Players.LocalPlayer;
                while true do
                    wait();
                    if l__LocalPlayer__1.Character then
                        break;
                    end;
                end;
                local l__Character__2 = l__LocalPlayer__1.Character;
                local l__Humanoid__3 = l__Character__2:WaitForChild("Humanoid");
                local l__Parent__4 = script.Parent;
                local u1 = false;
                local u2 = l__Humanoid__3:LoadAnimation(script.Hover);
                local u3 = nil;
                local u4 = nil;
                local u5 = false;
                local u6 = false;
                local u7 = l__Humanoid__3:LoadAnimation(script.Fly);
                l__Parent__4.Equipped:connect(function(p1)
                    Sound3:Play()
                    p1.TargetFilter = workspace;
                    u1 = true;
                    u2:Play();
                    u3 = Instance.new("BodyGyro");
                    u3.Name = "NA";
                    u3.Parent = l__Character__2.HumanoidRootPart;
                    u3.MaxTorque = Vector3.new(30000, 0, 30000);
                    u3.P = u3.P * 5;
                    u3.CFrame = CFrame.new(0, 0, 0);
                    u4 = Instance.new("BodyPosition");
                    u4.Name = "NA";
                    u4.Parent = l__Character__2.HumanoidRootPart;
                    u4.MaxForce = Vector3.new(60000, 60000, 60000);
                    u4.Position = l__Character__2.HumanoidRootPart.Position;
                    p1.Button1Down:connect(function()
                        Sound2:Play()
                        if u5 then
                            return;
                        end;
                        u5 = true;
                        u6 = true;
                        u7:Play();
                        local v5 = Instance.new("BodyVelocity", l__Character__2.HumanoidRootPart);
                        v5.MaxForce = Vector3.new(50000, 50000, 50000);
                        v5.Velocity = CFrame.new(l__Character__2.HumanoidRootPart.CFrame.p, p1.Hit.p).lookVector * 85;
                        u3.MaxTorque = Vector3.new(30000, 30000, 30000);
                        u3.CFrame = CFrame.new(l__Character__2.HumanoidRootPart.CFrame.p, p1.Hit.p);
                        u4.Parent = nil;
                        l__Humanoid__3.AutoRotate = false;
                        if u2.IsPlaying then
                            u2:Stop();
                        end;
                        while u6 do
                            v5.Velocity = CFrame.new(l__Character__2.HumanoidRootPart.CFrame.p, p1.Hit.p).lookVector * 85;
                            u3.CFrame = CFrame.new(l__Character__2.HumanoidRootPart.CFrame.p, p1.Hit.p);
                            game:GetService("RunService").Heartbeat:wait();		
                        end;
                        l__Humanoid__3.AutoRotate = true;
                        v5:Destroy();
                        if u4 ~= nil then
                            u4.Position = l__Character__2.HumanoidRootPart.Position;
                            u4.Parent = l__Character__2.HumanoidRootPart;
                        end;
                        if u3 ~= nil then
                            u3.MaxTorque = Vector3.new(30000, 0, 30000);
                            u3.CFrame = CFrame.new(0, 0, 0);
                        end;
                        u6 = false;
                        if u1 then
                            u2:Play();
                        end;
                        u7:Stop();
                        wait(0.3);
                        u5 = false;
                    end);
                    p1.Button1Up:connect(function()
                        Sound2:Stop()
                        Sound3:Play()
                        u6 = false;
                    end);
                end);
                l__Parent__4.Unequipped:connect(function()
                    Sound2:Stop()
                    Sound3:Play()
                    u1 = false;
                    u6 = false;
                    u3:Destroy();
                    u3 = nil;
                    u4:Destroy();
                    u4 = nil;
                    if u2.IsPlaying then
                        u2:Stop();
                    end;
                end);
            end))
            Sound2.Name = "Flapping"
            Sound2.Parent = LocalScript1
            Sound2.Looped = true
            Sound2.MaxDistance = 100
            Sound2.Pitch = 1.5
            Sound2.PlaybackSpeed = 1.5
            Sound2.SoundId = "rbxassetid://1462718291"
            Sound3.Name = "Activation"
            Sound3.Parent = LocalScript1
            Sound3.MaxDistance = 100
            Sound3.SoundId = "rbxassetid://2952274135"
            Sound3.Volume = 0.69999998807907
            Animation4.Name = "Hover"
            Animation4.Parent = LocalScript1
            Animation4.AnimationId = "rbxassetid://3541114300"
            RemoteEvent5.Name = "re"
            RemoteEvent5.Parent = LocalScript1
            Animation6.Name = "Fly"
            Animation6.Parent = LocalScript1
            Animation6.AnimationId = "rbxassetid://3541044388"
            for i,v in pairs(mas:GetChildren()) do
                v.Parent = game.Players.LocalPlayer.Backpack
                pcall(function() v:MakeJoints() end)
            end
            mas:Destroy()
            for i,v in pairs(cors) do
                spawn(function()
                    pcall(v)
                end)
            end
        end
        game.Players.LocalPlayer.Character:WaitForChild("FULLY_LOADED_CHAR")
        Fly()
end)





MainSection:NewButton("NoClip", "Now Exploiter Cant Fling ", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Noclip Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

 

power = 20 -- change this to make it more or less powerful

game:GetService('RunService').Stepped:connect(function()
game.Players.LocalPlayer.Character.Head.CanCollide = false
game.Players.LocalPlayer.Character.UpperTorso.CanCollide = false
game.Players.LocalPlayer.Character.LowerTorso.CanCollide = false
game.Players.LocalPlayer.Character.HumanoidRootPart.CanCollide = false
end)
wait(.1)

end)

MainSection:NewButton("Fe Spin", "Now Exploiter Cant Fling ", function()
    
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Spin Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
    
    local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

  

power = 50 -- change this to make it more or less powerful

game:GetService('RunService').Stepped:connect(function()
game.Players.LocalPlayer.Character.Head.CanCollide = false
game.Players.LocalPlayer.Character.UpperTorso.CanCollide = false
game.Players.LocalPlayer.Character.LowerTorso.CanCollide = false
game.Players.LocalPlayer.Character.HumanoidRootPart.CanCollide = false
end)
wait(.1)
local bambam = Instance.new("BodyThrust")
bambam.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart
bambam.Force = Vector3.new(power,0,power)
bambam.Location = game.Players.LocalPlayer.Character.HumanoidRootPart.Position


end)

HumanSection:NewButton("Spam Call", "call", function()
	game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Spam Call Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
	
	local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

local StarterGui = game:GetService("StarterGui")
for i,v in pairs(game.Players:GetChildren()) do
    if v.Name ~= game.Players.LocalPlayer.Name then
        game.Players.LocalPlayer.Backpack["[Phone]"].Parent = game.Players.LocalPlayer.Character
        game.ReplicatedStorage.MainEvent:FireServer("PhoneCall", tostring(v.Name))
        task.wait()
        game.Players.LocalPlayer.Character["[Phone]"].Parent = game.Players.LocalPlayer.Backpack
        task.wait()
        local success, result = pcall(StarterGui.SetCoreGuiEnabled, StarterGui, Enum.CoreGuiType.Backpack, true)
        task.wait(.2)
    end
end 

end)



testSection:NewButton("Auto Arrest", "auto arrest", function()
game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Auto Arrest Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
	
	local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()


wait(0.5); if _G.AutoArrest == false or game.PlaceId ~= 2788229376 then return else repeat wait() until game.Players.LocalPlayer end

for i, v in next, game.Workspace:GetDescendants() do
	if v:IsA("Seat") then
		v:Destroy()
	end
end

local Plr = game.Players.LocalPlayer

function serverhop()

    print("PENIS")
	Plr:Destroy()
	local x = {}
	for _, v in ipairs(game:GetService("HttpService"):JSONDecode(game:HttpGetAsync("https://games.roblox.com/v1/games/" .. game.PlaceId .. "/servers/Public?sortOrder=Asc&limit=100")).data) do
		if type(v) == "table" and v.maxPlayers > v.playing and v.id ~= game.JobId then
			x[#x + 1] = v.id
		end
	end
	if #x > 0 then
		game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, x[math.random(1, #x)])
	end
end


spawn(function()
    wait(300)
    serverhop()
end)

game:GetService("RunService").Stepped:connect(function()
    Plr.Character.Humanoid:ChangeState(11)
end)
Plr.CharacterAdded:Connect(function(character)
    repeat wait() until character:FindFirstChild("FULLY_LOADED_CHAR")
    e(character)
end)
function e(character)
    for i, v in pairs(game.Workspace.Ignored.ItemsDrop:GetChildren()) do
        if v:FindFirstChild("[Knife]") and Plr.Character:FindFirstChild("[Knife]") == nil and Plr.Backpack:FindFirstChild("[Knife]") == nil then
            Plr.Character.HumanoidRootPart.CFrame = v.CFrame
            wait(1)
        end
    end
    for i, v in pairs(character:GetChildren()) do
        if v:FindFirstChild("LocalScript") then
            v:Destroy()
        end
    end
end

e(Plr.character)
local target
while wait() do
    target = nil
    local highest = 0
    for i, v in pairs(game.Players:GetPlayers()) do
        if v:FindFirstChild("DataFolder") and v.Character:FindFirstChild("FULLY_LOADED_CHAR") and v.Character.BodyEffects:FindFirstChild("Defense") and tonumber(v.DataFolder.Information.Wanted.Value) > 500 and tonumber(v.DataFolder.Information.Wanted.Value) >= highest and v.Character.BodyEffects:FindFirstChild("Armor") then
            target = v 
            highest = tonumber(v.DataFolder.Information.Wanted.Value)
        end
    end
    if not target then serverhop() end
    local e = true
    local penis = 0
    local bagged = true
    local A = false
    spawn(function() pcall(function()
        while bagged == true do
            if target and target.Character and target.Character:FindFirstChild("Christmas_Sock") == nil and penis <= 5 and Plr.Character.Humanoid.Health > 80 then
                if Plr.Backpack:FindFirstChild("[BrownBag]") == nil then
                    A = false
                    pcall(function()
                        repeat wait()
                            Plr.character.HumanoidRootPart.CFrame = CFrame.new(-316.034454, 48.2788467, -723.860474, 0.983254969, -0.000297372608, -0.182234928, 0.000218386791, 0.999999881, -0.000453495246, 0.182235047, 0.000406103791, 0.98325491)
                            fireclickdetector(game:GetService("Workspace").Ignored.Shop["[BrownBag] - $25"].ClickDetector)
                        until Plr.Backpack:FindFirstChild("[BrownBag]") ~= nil
                    end)
                    A = true
                end
                Plr.Character.Humanoid:EquipTool(Plr.Backpack["[BrownBag]"])
                Plr.Character["[BrownBag]"]:Activate()
                penis = penis + 1
            elseif penis >= 2 or target.Character:FindFirstChild("Christmas_Sock") or not target then
                bagged = true
            end
            wait(3)
        end
    end) end)
    spawn(function()
        while e do wait()
            pcall(function()
                if Plr.Character.Humanoid.Health > 80 then
                    if not target.Character.BodyEffects["K.O"].Value then
                        if A then
                            Plr.Character.HumanoidRootPart.CFrame = CFrame.new(target.Character.UpperTorso.Position + Vector3.new(0, -5, 0))
                        end
                    else
                        Plr.Character.HumanoidRootPart.CFrame = target.Character.UpperTorso.CFrame
                    end
                else
                    Plr.Character.HumanoidRootPart.CFrame = CFrame.new(0, 999, 0)
                    if Plr.Character:FindFirstChild("[Taco]") == nil or Plr.Backpack:FindFirstChild("[Taco]") == nil then
                        Plr.Character.HumanoidRootPart.CFrame = game.Workspace.Ignored.Shop["[Taco] - $2"].Head.CFrame
                        wait(0.5)
                        fireclickdetector(game.Workspace.Ignored.Shop["[Taco] - $2"].ClickDetector)
                    end
                    pcall(function()Plr.Character.Humanoid:EquipTool(Plr.Backpack["[Taco]"])end)
                    pcall(function()
                        Plr.Character["[Taco]"]:Activate()
                        wait(0.1)
                        Plr.Character["[Taco]"]:Deactivate()
                    end)
                end
            end)
        end
    end)
    repeat wait() until bagged
    pcall(function()
        repeat wait()
            repeat wait()
                pcall(function()
                if Plr.Character.Humanoid.Health > 80 then
                    pcall(function()Plr.Character.Humanoid:EquipTool(Plr.Backpack["[Knife]"])end)
                    wait(0.1)
                        Plr.Character["[Knife]"].GripPos = Vector3.new(0, 5, 0)
                        Plr.Character["[Knife]"].Handle.Size = Vector3.new(20, 20, 20)
                        Plr.Character["[Knife]"]:Activate()
                        wait(1.25)
                        Plr.Character["[Knife]"]:Deactivate()
                        wait(1.25)
                    end
                end)
            until not target or target.Character.BodyEffects["K.O"].Value or game:GetService("UserInputService"):IsKeyDown(Enum.KeyCode.V)
            repeat wait() 
                if Plr.Character.Humanoid.Health > 80 then
                    pcall(function()Plr.Character.Humanoid:EquipTool(Plr.Backpack.Cuff)end)
                    pcall(function()
                        wait(.1)
                        Plr.Character.Cuff:Activate()
                        wait(.1)
                        Plr.Character.Cuff:Deactivate()
                    end)
                end
            until not target.Character.BodyEffects["K.O"].Value or game:GetService("UserInputService"):IsKeyDown(Enum.KeyCode.V)
        until tonumber(target.DataFolder.Information.Wanted.Value) == 0 or game:GetService("UserInputService"):IsKeyDown(Enum.KeyCode.V)
    end)
    e = false
end
end)

testSection:NewButton("Anti Cheat Bypass V1", "auto arrest", function()
game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Anti Cheat Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
	
	local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

if not game:IsLoaded() then
    game.Loaded:wait()
end

local placeId = game.PlaceId;
if placeId ~= 2788229376 and placeId ~= 7213786345 then
    return;
end -- remove this if you want to use this on another game that isnt da hood

-- This script prevents client anti cheats from detecting guis
-- Place in autoexec folder

local MetamethodHolder = {
    AntiFlag = nil
}

MetamethodHolder.AntiFlag = hookmetamethod(game, "__namecall", function(self, ...)
    local Method = getnamecallmethod()
    if tostring(Method) == "PreloadAsync" and not checkcaller() then
        return
    end    
   
    return MetamethodHolder.AntiFlag(self, ...)    
end)


-- // Services
local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- // Vars
local tablefind = table.find
local MainEvent = ReplicatedStorage.MainEvent
local SpoofTable = {
    WalkSpeed = 16,
    JumpPower = 50
}

-- // Configuration
local Flags = {
    "CHECKER_1",
    "TeleportDetect",
    "OneMoreTime"
}

-- // __namecall hook
local __namecall
__namecall = hookmetamethod(game, "__namecall", function(...)
    -- // Vars
    local args = {...}
    local self = args[1]
    local method = getnamecallmethod()
    local caller = getcallingscript()

    -- // See if the game is trying to alert the server
    if (method == "FireServer" and self == MainEvent and tablefind(Flags, args[2])) then
        return
    end

  
    
    -- //
    return __namecall(...)
end)

-- // __index hook
local __index
__index = hookmetamethod(game, "__index", function(t, k)
    -- // Make sure it's trying to get our humanoid's ws/jp
    if (not checkcaller() and t:IsA("Humanoid") and (k == "WalkSpeed" or k == "JumpPower")) then
        -- // Return spoof values
        return SpoofTable[k]
    end

    -- //
    return __index(t, k)
end)

-- // __newindex hook
local __newindex
__newindex = hookmetamethod(game, "__newindex", function(t, k, v)
    -- // Make sure it's trying to set our humanoid's ws/jp
    if (not checkcaller() and t:IsA("Humanoid") and (k == "WalkSpeed" or k == "JumpPower")) then
        -- // Add values to spoof table
        SpoofTable[k] = v

        -- // Disallow the set
        return
    end
    
    -- //
    return __newindex(t, k, v)
end)

end)


testSection:NewButton("Anti Cheat Bypass V2", "auto arrest", function()
game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Anti Cheat Bypass Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
	
	local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

repeat wait() until game:IsLoaded()



assert(getrawmetatable)
grm = getrawmetatable(game)
setreadonly(grm, false)
old = grm.__namecall
grm.__namecall = newcclosure(function(self, ...)
    local args = {...}
    if tostring(args[1]) == "TeleportDetect" then
        return
    elseif tostring(args[1]) == "CHECKER_1" then
        return
    elseif tostring(args[1]) == "CHECKER" then
        return
    elseif tostring(args[1]) == "GUI_CHECK" then
        return
    elseif tostring(args[1]) == "OneMoreTime" then
        return
    elseif tostring(args[1]) == "checkingSPEED" then
        return
    elseif tostring(args[1]) == "BANREMOTE" then
        return
    elseif tostring(args[1]) == "PERMAIDBAN" then
        return
    elseif tostring(args[1]) == "KICKREMOTE" then
        return
    elseif tostring(args[1]) == "BR_KICKPC" then
        return
    elseif tostring(args[1]) == "BR_KICKMOBILE" then
        return
    end
    return old(self, ...)
end)

end)




scriptwareSection:NewButton("Anti Lock (Sky)", "aimlock", function()
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Anti Lock Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
      
      
      local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()

getgenv().Sky = true 
getgenv().SkyAmount = 1600

game:GetService("RunService").heartbeat:Connect(function()
    if getgenv().Sky ~= false then 
    local vel = game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity
    game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(0,      getgenv().SkyAmount,0) 
    game:GetService("RunService").RenderStepped:Wait()
    game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = vel
    end 
end)
end)




scriptwareSection:NewButton("Anti Lock (UnderGround)", "aimlock", function()
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Anti Lock Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
      
      
      local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()
getgenv().Underground = true 
getgenv().UndergroundAmount = 1000

game:GetService("RunService").heartbeat:Connect(function()
    if getgenv().Underground ~= false then 
    local vel = game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity
    game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(0,-         getgenv().UndergroundAmount,0) 
    game:GetService("RunService").RenderStepped:Wait()
    game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = vel
    end 
end)

end)




scriptwareSection:NewButton("Anti Lock (Resolver)", "aimlock", function()
     game.StarterGui:SetCore("SendNotification", {Title = "Bacon X ", Text = "Anti Resolver Loaded", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "OK"})
      local RunService = game:GetService("RunService")

RunService.Heartbeat:Connect(function()
    pcall(function()
        for i,v in pairs(game.Players:GetChildren()) do
            if v.Name ~= game.Players.LocalPlayer.Name then
                local hrp = v.Character.HumanoidRootPart
                hrp.Velocity = Vector3.new(hrp.Velocity.X, 0, hrp.Velocity.Z)    
                hrp.AssemblyLinearVelocity = Vector3.new(hrp.Velocity.X, 0, hrp.Velocity.Z)   
            end
        end
    end)
end)
      
      local Sound = Instance.new("Sound", workspace)
Sound.SoundId = "rbxassetid://1092093337"
Sound:Play()


end)

extraSection:NewKeybind("Toggle Gui", "hide script", Enum.KeyCode.F, function()
Library:ToggleUI()
end)
