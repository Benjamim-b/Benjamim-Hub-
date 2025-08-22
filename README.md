-- Painel de ADM (Kick e Kill)
-- Funciona com loadstring do GitHub

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- GUI principal
local screenGui = Instance.new("ScreenGui", game.CoreGui)
screenGui.Name = "AdminPanelGUI"

-- Botão ícone
local iconButton = Instance.new("TextButton", screenGui)
iconButton.Text = "Admin🤑"
iconButton.Size = UDim2.new(0, 50, 0, 50)
iconButton.Position = UDim2.new(0, 10, 0, 10)
iconButton.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
iconButton.TextColor3 = Color3.fromRGB(255, 255, 255)

local iconCorner = Instance.new("UICorner", iconButton)
iconCorner.CornerRadius = UDim.new(0, 10)

-- Painel ADM
local hubFrame = Instance.new("Frame", screenGui)
hubFrame.Size = UDim2.new(0, 300, 0, 180)
hubFrame.Position = UDim2.new(0.5, -150, 0.5, -90)
hubFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
hubFrame.Visible = false

local hubCorner = Instance.new("UICorner", hubFrame)
hubCorner.CornerRadius = UDim.new(0, 15)

-- Título
local title = Instance.new("TextLabel", hubFrame)
title.Text = "Painel de ADM"
title.Size = UDim2.new(1, 0, 0, 40)
title.BackgroundTransparency = 1
title.TextColor3 = Color3.fromRGB(255, 255, 0)
title.Font = Enum.Font.FredokaOne
title.TextScaled = true

-- Função para criar botões
local function criarBotao(nome, pos, callback)
    local btn = Instance.new("TextButton", hubFrame)
    btn.Size = UDim2.new(0, 200, 0, 40)
    btn.Position = UDim2.new(0.5, -100, 0, pos)
    btn.Text = nome
    btn.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
    btn.TextColor3 = Color3.fromRGB(255, 255, 255)
    btn.Font = Enum.Font.SourceSansBold
    btn.TextSize = 20

    local corner = Instance.new("UICorner", btn)
    corner.CornerRadius = UDim.new(0, 10)

    btn.MouseButton1Click:Connect(callback)
end

-- Funções do ADM
local function kickPlayer()
    local targetName = Players:GetPlayers()[2] -- Pega o 2º player (exemplo)
    if targetName then
        targetName:Kick("Tchau! Você foi expulso.")
    end
end

local function killPlayer()
    local targetName = Players:GetPlayers()[2] -- Pega o 2º player (exemplo)
    if targetName and targetName.Character and targetName.Character:FindFirstChild("Humanoid") then
        targetName.Character.Humanoid.Health = 0
    end
end

-- Criar botões
criarBotao("Kick", 60, kickPlayer)
criarBotao("Kill", 110, killPlayer)

-- Abrir/fechar Hub
local hubAberto = false
iconButton.MouseButton1Click:Connect(function()
    hubAberto = not hubAberto
    hubFrame.Visible = hubAberto
end)
