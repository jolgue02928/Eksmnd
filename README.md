-- Jolgue Hub (Auto Clicker 15x/s)

local Players = game:GetService("Players")
local player = Players.LocalPlayer
local RunService = game:GetService("RunService")

-- GUI Setup
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "JolgueHub"
screenGui.Parent = player:WaitForChild("PlayerGui")

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 200, 0, 100)
frame.Position = UDim2.new(0, 20, 0, 100)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame.BorderSizePixel = 0
frame.Active = true
frame.Draggable = true
frame.Parent = screenGui

local title = Instance.new("TextLabel")
title.Text = "Jolgue Hub (auto_click)"
title.Size = UDim2.new(1, 0, 0, 30)
title.BackgroundTransparency = 1
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Font = Enum.Font.Gotham
title.TextSize = 16
title.Parent = frame

local toggle = Instance.new("TextButton")
toggle.Text = "Ativar Auto Click"
toggle.Size = UDim2.new(1, -20, 0, 40)
toggle.Position = UDim2.new(0, 10, 0, 40)
toggle.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
toggle.TextColor3 = Color3.fromRGB(255, 255, 255)
toggle.Font = Enum.Font.GothamBold
toggle.TextSize = 14
toggle.Parent = frame

-- Auto clicker toggle
local clicking = false
toggle.MouseButton1Click:Connect(function()
	clicking = not clicking
	toggle.Text = clicking and "Desativar Auto Click" or "Ativar Auto Click"
end)

-- ⚠️ Substitua esta função pela ação de clique do seu jogo
local function doClick()
	-- Exemplo genérico: substitua abaixo
	-- game:GetService("ReplicatedStorage").ClickRemote:FireServer()
	print("Clique automático executado")
end

-- Início do loop de cliques
task.spawn(function()
	while true do
		if clicking then
			doClick()
		end
		task.wait(1 / 15) -- 15 vezes por segundo
	end
end)
