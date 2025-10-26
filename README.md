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
