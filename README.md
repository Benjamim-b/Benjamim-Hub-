-- // Panel de ADM by Benjamim Hub
-- // Feito para rodar via loadstring do GitHub

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- // Criar ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "AdminPanel"
screenGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

-- // Botão Ícone (abrir/fechar Hub)
local iconButton = Instance.new("TextButton")
iconButton.Name = "IconButton"
iconButton.Size = UDim2.new(0, 50, 0, 50)
iconButton.Position = UDim2.new(0, 10, 0, 200)
iconButton.Text = "≡"
iconButton.Parent = screenGui

local iconCorner = Instance.new("UICorner")
iconCorner.CornerRadius = UDim.new(0, 8)
iconCorner.Parent = iconButton

-- // Hub principal
local hubFrame = Instance.new("Frame")
hubFrame.Name = "HubFrame"
hubFrame.Size = UDim2.new(0, 300, 0, 200)
hubFrame.Position = UDim2.new(0.5, -150, 0.5, -100)
hubFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
hubFrame.Visible = false
hubFrame.Parent = screenGui

local hubCorner = Instance.new("UICorner")
hubCorner.CornerRadius = UDim.new(0, 12)
hubCorner.Parent = hubFrame

-- // Título
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 40)
title.BackgroundTransparency = 1
title.Text = "Panel de ADM"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Font = Enum.Font.SourceSansBold
title.TextSize = 24
title.Parent = hubFrame

-- // Funções Kick e Kill
local function kickPlayer(name)
    local target = Players:FindFirstChild(name)
    if target then
        target:Kick("Tchau 👋")
    end
end

local function killPlayer(name)
    local target = Players:FindFirstChild(name)
    if target and target.Character and target.Character:FindFirstChild("Humanoid") then
        target.Character.Humanoid.Health = 0
    end
end

-- // Botão Kick
local kickButton = Instance.new("TextButton")
kickButton.Size = UDim2.new(0, 120, 0, 40)
kickButton.Position = UDim2.new(0.1, 0, 0.4, 0)
kickButton.Text = "Kick (;kick Nome)"
kickButton.Parent = hubFrame

local kickCorner = Instance.new("UICorner")
kickCorner.CornerRadius = UDim.new(0, 8)
kickCorner.Parent = kickButton

kickButton.MouseButton1Click:Connect(function()
    local name = game:GetService("Players"):GetPlayers()[2] -- exemplo: pega o segundo player
    if name then
        kickPlayer(name.Name)
    end
end)

-- // Botão Kill
local killButton = Instance.new("TextButton")
killButton.Size = UDim2.new(0, 120, 0, 40)
killButton.Position = UDim2.new(0.55, 0, 0.4, 0)
killButton.Text = "Kill (;kill Nome)"
killButton.Parent = hubFrame

local killCorner = Instance.new("UICorner")
killCorner.CornerRadius = UDim.new(0, 8)
killCorner.Parent = killButton

killButton.MouseButton1Click:Connect(function()
    local name = game:GetService("Players"):GetPlayers()[2] -- exemplo: pega o segundo player
    if name then
        killPlayer(name.Name)
    end
end)

-- // Abrir/fechar o Hub
local isOpen = false
iconButton.MouseButton1Click:Connect(function()
    isOpen = not isOpen
    hubFrame.Visible = isOpen
end)

print("✅ Panel de ADM carregado com sucesso!")
