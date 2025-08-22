--// Benjamim Hub 😊
-- Script para ser usado via loadstring do GitHub

--// Serviços
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

--// ScreenGui principal
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "BenjamimHubGUI"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

--// Ícone do Hub
local iconButton = Instance.new("TextButton")
iconButton.Name = "IconButton"
iconButton.Text = "≡" -- símbolo de menu
iconButton.Size = UDim2.new(0, 50, 0, 50)
iconButton.Position = UDim2.new(0, 10, 0, 10)
iconButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
iconButton.TextColor3 = Color3.fromRGB(255, 255, 255)
iconButton.Font = Enum.Font.SourceSansBold
iconButton.TextSize = 28
iconButton.Parent = screenGui

local iconCorner = Instance.new("UICorner")
iconCorner.CornerRadius = UDim.new(0, 10)
iconCorner.Parent = iconButton

--// Tela de carregamento
local loadingFrame = Instance.new("Frame")
loadingFrame.Size = UDim2.new(1, 0, 1, 0)
loadingFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
loadingFrame.Visible = false
loadingFrame.ZIndex = 5
loadingFrame.Parent = screenGui

local hubTitle = Instance.new("TextLabel")
hubTitle.Text = "Benjamim Hub 😊"
hubTitle.Size = UDim2.new(1, 0, 0, 100)
hubTitle.Position = UDim2.new(0, 0, 0.4, 0)
hubTitle.TextScaled = true
hubTitle.TextColor3 = Color3.fromRGB(255, 255, 0)
hubTitle.BackgroundTransparency = 1
hubTitle.Font = Enum.Font.FredokaOne
hubTitle.ZIndex = 6
hubTitle.Parent = loadingFrame

--// Hub principal
local hubFrame = Instance.new("Frame")
hubFrame.Size = UDim2.new(0, 300, 0, 200)
hubFrame.Position = UDim2.new(0.5, -150, 0.5, -100)
hubFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
hubFrame.Visible = false
hubFrame.Parent = screenGui

local hubCorner = Instance.new("UICorner")
hubCorner.CornerRadius = UDim.new(0, 15)
hubCorner.Parent = hubFrame

-- Botão de exemplo dentro do Hub
local exampleButton = Instance.new("TextButton")
exampleButton.Size = UDim2.new(0, 100, 0, 50)
exampleButton.Position = UDim2.new(0.5, -50, 0.5, -25)
exampleButton.Text = "Oi"
exampleButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
exampleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
exampleButton.Font = Enum.Font.SourceSansBold
exampleButton.TextSize = 20
exampleButton.Parent = hubFrame

local exampleCorner = Instance.new("UICorner")
exampleCorner.CornerRadius = UDim.new(0, 10)
exampleCorner.Parent = exampleButton

--// Lógica abrir/fechar com carregamento
local hubAberto = false
iconButton.MouseButton1Click:Connect(function()
	if hubAberto then
		-- Fechar
		hubFrame.Visible = false
		hubAberto = false
	else
		-- Abrir com loading
		loadingFrame.Visible = true
		hubFrame.Visible = false

		task.wait(2) -- tempo da tela de carregamento

		loadingFrame.Visible = false
		hubFrame.Visible = true
		hubAberto = true
	end
end)
