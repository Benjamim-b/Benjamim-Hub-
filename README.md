-- Script Hub com ícone arredondado e botão
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Criando a GUI principal
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "ScriptHubUI"
screenGui.Parent = playerGui
screenGui.ResetOnSpawn = false

-- Criando ícone de abrir/fechar
local iconButton = Instance.new("TextButton")
iconButton.Name = "Icon"
iconButton.Text = "≡"
iconButton.Size = UDim2.new(0, 50, 0, 50)
iconButton.Position = UDim2.new(0, 20, 0, 200)
iconButton.BackgroundColor3 = Color3.fromRGB(70, 130, 250)
iconButton.TextColor3 = Color3.fromRGB(255, 255, 255)
iconButton.Parent = screenGui

local cornerIcon = Instance.new("UICorner")
cornerIcon.CornerRadius = UDim.new(0, 12)
cornerIcon.Parent = iconButton

-- Criando o Hub
local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 400, 0, 250)
mainFrame.Position = UDim2.new(0.5, -200, 0.5, -125)
mainFrame.BackgroundColor3 = Color3.fromRGB(240, 240, 240)
mainFrame.Visible = false
mainFrame.Parent = screenGui

local cornerMain = Instance.new("UICorner")
cornerMain.CornerRadius = UDim.new(0, 15)
cornerMain.Parent = mainFrame

-- Título
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 40)
title.BackgroundTransparency = 1
title.Text = "Script Hub"
title.TextScaled = true
title.TextColor3 = Color3.fromRGB(0, 0, 0)
title.Parent = mainFrame

-- Botão de exemplo
local exampleBtn = Instance.new("TextButton")
exampleBtn.Size = UDim2.new(0, 200, 0, 40)
exampleBtn.Position = UDim2.new(0.5, -100, 0.5, -20)
exampleBtn.Text = "Botão de Teste"
exampleBtn.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
exampleBtn.TextColor3 = Color3.fromRGB(0, 0, 0)
exampleBtn.Parent = mainFrame

local cornerBtn = Instance.new("UICorner")
cornerBtn.CornerRadius = UDim.new(0, 10)
cornerBtn.Parent = exampleBtn

-- Função do botão de teste
exampleBtn.MouseButton1Click:Connect(function()
    print("Botão de Teste clicado!")
end)

-- Alternar Hub
local open = false
iconButton.MouseButton1Click:Connect(function()
    open = not open
    mainFrame.Visible = open
end)
