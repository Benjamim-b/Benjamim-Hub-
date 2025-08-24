-- Gui Script com loadstring (coloque no GitHub)
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- ScreenGui principal
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "ScriptHub"
screenGui.Parent = playerGui

-- Ícone abrir/fechar
local iconButton = Instance.new("TextButton")
iconButton.Name = "Icon"
iconButton.Size = UDim2.new(0, 80, 0, 30)
iconButton.Position = UDim2.new(0, 10, 0, 10)
iconButton.Text = "Script Hub"
iconButton.TextColor3 = Color3.fromRGB(255, 255, 255)
iconButton.BackgroundColor3 = Color3.fromRGB(0, 102, 204)
iconButton.Parent = screenGui

-- UICorner no ícone
local iconCorner = Instance.new("UICorner")
iconCorner.CornerRadius = UDim.new(0, 10)
iconCorner.Parent = iconButton

-- Frame do Hub
local hubFrame = Instance.new("Frame")
hubFrame.Size = UDim2.new(0, 500, 0, 300)
hubFrame.Position = UDim2.new(0.5, -250, 0.5, -150)
hubFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0) -- Fundo preto
hubFrame.Visible = false
hubFrame.Parent = screenGui

-- UICorner do Hub
local hubCorner = Instance.new("UICorner")
hubCorner.CornerRadius = UDim.new(0, 15)
hubCorner.Parent = hubFrame

-- Texto principal
local title = Instance.new("TextLabel")
title.Size = UDim2.new(0, 300, 0, 50)
title.Position = UDim2.new(0.5, -150, 0, 20)
title.Text = "O meu servidor do discord"
title.TextScaled = true
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
title.Parent = hubFrame

local titleCorner = Instance.new("UICorner")
titleCorner.CornerRadius = UDim.new(0, 10)
titleCorner.Parent = title

-- Criar botões laterais (5 botões)
for i = 1, 5 do
    local sideButton = Instance.new("TextButton")
    sideButton.Size = UDim2.new(0, 120, 0, 40)
    sideButton.Position = UDim2.new(0, 20, 0, 20 + (i * 50))
    sideButton.Text = "Botão " .. i
    sideButton.TextColor3 = Color3.fromRGB(0, 0, 0)
    sideButton.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
    sideButton.Parent = hubFrame
    
    local sideCorner = Instance.new("UICorner")
    sideCorner.CornerRadius = UDim.new(0, 8)
    sideCorner.Parent = sideButton
end

-- Botão do meio
local centerButton = Instance.new("TextButton")
centerButton.Size = UDim2.new(0, 200, 0, 50)
centerButton.Position = UDim2.new(0.5, -100, 0.5, 0)
centerButton.Text = "Clique Aqui"
centerButton.TextColor3 = Color3.fromRGB(0, 0, 0)
centerButton.BackgroundColor3 = Color3.fromRGB(200, 200, 200)
centerButton.Parent = hubFrame

local centerCorner = Instance.new("UICorner")
centerCorner.CornerRadius = UDim.new(0, 10)
centerCorner.Parent = centerButton

-- Função abrir/fechar
iconButton.MouseButton1Click:Connect(function()
    hubFrame.Visible = not hubFrame.Visible
end)
