--// Script Hub - Painel com Ícone e Hub
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

--// Criando ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "ScriptHubGui"
screenGui.Parent = playerGui

--// Ícone (botão para abrir/fechar)
local iconButton = Instance.new("TextButton")
iconButton.Name = "Icon"
iconButton.Size = UDim2.new(0, 100, 0, 40)
iconButton.Position = UDim2.new(0, 20, 0, 200)
iconButton.Text = "Script Hub"
iconButton.BackgroundColor3 = Color3.fromRGB(65, 130, 255)
iconButton.TextColor3 = Color3.fromRGB(255, 255, 255)
iconButton.Parent = screenGui

-- Deixar o botão arredondado
local uicorner = Instance.new("UICorner")
uicorner.CornerRadius = UDim.new(0, 12)
uicorner.Parent = iconButton

--// Hub principal
local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 400, 0, 250)
mainFrame.Position = UDim2.new(0.5, -200, 0.5, -125)
mainFrame.BackgroundColor3 = Color3.fromRGB(245, 245, 245)
mainFrame.Visible = false
mainFrame.Parent = screenGui

local mainCorner = Instance.new("UICorner")
mainCorner.CornerRadius = UDim.new(0, 12)
mainCorner.Parent = mainFrame

--// Título
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, -20, 0, 50)
title.Position = UDim2.new(0, 10, 0, 10)
title.BackgroundTransparency = 1
title.Text = "O meu servidor do discord"
title.TextColor3 = Color3.fromRGB(50, 50, 50)
title.Font = Enum.Font.SourceSansBold
title.TextSize = 20
title.Parent = mainFrame

--// Botão dentro do hub
local hubButton = Instance.new("TextButton")
hubButton.Size = UDim2.new(0, 150, 0, 50)
hubButton.Position = UDim2.new(0.5, -75, 0.5, -25)
hubButton.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
hubButton.Text = "Botão"
hubButton.Parent = mainFrame

local hubCorner = Instance.new("UICorner")
hubCorner.CornerRadius = UDim.new(0, 12)
hubCorner.Parent = hubButton

--// Funções abrir/fechar
iconButton.MouseButton1Click:Connect(function()
    mainFrame.Visible = not mainFrame.Visible
end)

hubButton.MouseButton1Click:Connect(function()
    print("Botão dentro do Hub foi clicado!")
end)
