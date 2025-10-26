local functions = {
  rconsoleprint,
  print,
  setclipboard,
  rconsoleerr,
  rconsolewarn,
  warn,
  error
}

game:GetService('RunService').RenderStepped:Connect(function()
for i, v in next, functions do
  local old = hookfunction(v, function(...)
   local args = {...}
   for i, v in next, args do
     if tostring(i):find("https://") or tostring(v):find("https://") then
       game.Players.LocalPlayer:Kick("HttpSpy Detected!")
     end
   end
   return old(...)
  end)
end
end)

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
