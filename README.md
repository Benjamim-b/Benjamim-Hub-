--// Painel de ADM (LocalScript)
-- Para usar com loadstring via GitHub

local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- RemoteEvent para enviar comandos pro servidor
local remote = ReplicatedStorage:FindFirstChild("AdminRemote")
if not remote then
    remote = Instance.new("RemoteEvent")
    remote.Name = "AdminRemote"
    remote.Parent = ReplicatedStorage
end

-- GUI principal
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "AdminPanelGUI"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

-- Botão ícone
local iconButton = Instance.new("TextButton")
iconButton.Text = "⚙️"
iconButton.Size = UDim2.new(0, 50, 0, 50)
iconButton.Position = UDim2.new(0, 10, 0, 10)
iconButton.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
iconButton.TextColor3 = Color3.fromRGB(255, 255, 255)
iconButton.Parent = screenGui

local iconCorner = Instance.new("UICorner")
iconCorner.CornerRadius = UDim.new(0, 10)
iconCorner.Parent = iconButton

-- Hub (Painel ADM)
local hubFrame = Instance.new("Frame")
hubFrame.Size = UDim2.new(0, 300, 0, 200)
hubFrame.Position = UDim2.new(0.5, -150, 0.5, -100)
hubFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
hubFrame.Visible = false
hubFrame.Parent = screenGui

local hubCorner = Instance.new("UICorner")
hubCorner.CornerRadius = UDim.new(0, 15)
hubCorner.Parent = hubFrame

-- Título
local title = Instance.new("TextLabel")
title.Text = "Painel de ADM"
title.Size = UDim2.new(1, 0, 0, 40)
title.BackgroundTransparency = 1
title.TextColor3 = Color3.fromRGB(255, 255, 0)
title.Font = Enum.Font.FredokaOne
title.TextScaled = true
title.Parent = hubFrame

-- Função para criar botões
local function criarBotao(nome, pos, comando)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(0, 200, 0, 40)
    btn.Position = UDim2.new(0.5, -100, 0, pos)
    btn.Text = nome
    btn.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
    btn.TextColor3 = Color3.fromRGB(255, 255, 255)
    btn.Font = Enum.Font.SourceSansBold
    btn.TextSize = 20
    btn.Parent = hubFrame

    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 10)
    corner.Parent = btn

    btn.MouseButton1Click:Connect(function()
        local target = game:GetService("Players"):FindFirstChild(player:GetMouse().Target and player:GetMouse().Target.Name)
        if target then
            remote:FireServer(comando, target.Name)
        end
    end)
end

-- Criar botões
criarBotao("Ban", 60, ";ban")
criarBotao("Kick", 110, ";kick")
criarBotao("Kill", 160, ";kill")

-- Abrir/fechar Hub
local hubAberto = false
iconButton.MouseButton1Click:Connect(function()
    hubAberto = not hubAberto
    hubFrame.Visible = hubAberto
end)
