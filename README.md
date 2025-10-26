local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/realredz/RedzLibV5/main/Source.lua"))()

local Window = Library:MakeWindow({
Title = "Catholic Hub | Blox Fruits",
SubTitle = "by Denolk and Vloxer Studio // 1.1",
SaveFolder = "CatholicHubFold"
})

Window:AddMinimizeButton({
Button = { Image = "rbxassetid://rbxassetid://134315256405587", BackgroundTransparency = 0 },
Corner = { CornerRadius = UDim.new(35, 1) },
})
---//Credits
local Tab = Window:MakeTab({
Title = "Credits",
Icon = "Home" 
})

local DiscordInvite = Tab:AddDiscordInvite({
    Title = "Catholic Hub | Community",
    Desc = "Join Discord For News Hub", 
    Logo = "rbxassetid://99552187299228", 
    Invite = "https://discord.gg/2ZhUmbKp" 
})


local Paragraph = Tab:AddParagraph({
    Title = "Hey",
    Text = "Join Discord For News Off Hub!"
})


Tab:AddSection({ "Script Information" })


local function createInfoBlock(tab, title, initial)
	local block
	local ok = pcall(function()
		block = tab:AddParagraph({ Title = title, Content = initial })
	end)
	if not ok or not block then
		ok = pcall(function()
			block = tab:AddLabel(title .. (initial and ("\n" .. initial) or ""))
		end)
	end
	return block
end

local function setBlockText(block, title, text)
	if not block then return end
	local ok = pcall(function()
		if block.Set then return block:Set(text) end
		if block.SetDesc then return block:SetDesc(text) end
		if block.SetText then return block:SetText(text) end
		if block.Update then return block:Update(text) end
		if block.Refresh then return block:Refresh(text) end
	end)
	if not ok then
		pcall(function()
			if block.Text ~= nil then
				block.Text = title .. "\n" .. text
			end
		end)
	end
end

local function getCurrentDate()
	local currentTime = os.time()
	return os.date("%d/%m/%Y", currentTime)
end

local Players = game:GetService("Players")
local localPlayer = Players.LocalPlayer

local welcomeBlock = createInfoBlock(Tab, "Welcome! Today is: ", getCurrentDate())

Tab:AddParagraph({"Your Nickname: " .. (game.Players.LocalPlayer.Name or "Unknown")})

Tab:AddParagraph({"Your ID: " .. tostring(game.Players.LocalPlayer.UserId or 0)})

local timerBlock   = createInfoBlock(Tab, "Script Usage Time: ", "00:00:00")
local fpsBlock     = createInfoBlock(Tab, "Your FPS: ", "FPS: 0")

local RunService = game:GetService("RunService")

local startClock = os.clock()

local currentFPS = 0
RunService.RenderStepped:Connect(function(dt)
	currentFPS = math.floor(1/dt + 0.5)
end)

task.spawn(function()
	while true do
		task.wait(0.5)

		setBlockText(welcomeBlock, "Welcome! Today is: ", getCurrentDate())

		local e = os.clock() - startClock
		local h = math.floor(e/3600)
		local m = math.floor((e%3600)/60)
		local s = math.floor(e%60)
		setBlockText(timerBlock, "Script Usage Time: ", string.format("%02d:%02d:%02d", h, m, s))

		setBlockText(fpsBlock, "Your FPS: ", "FPS: " .. tostring(currentFPS))
	end
end)
