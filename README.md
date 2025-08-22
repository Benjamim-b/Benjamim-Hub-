-- Panel de ADM completo para loadstring
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local PlayerGui = LocalPlayer:WaitForChild("PlayerGui")

-- ======== Tela de Carregamento ========
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "AdminPanel"
screenGui.Parent = PlayerGui

local loadingFrame = Instance.new("Frame")
loadingFrame.Size = UDim2.new(1,0,1,0)
loadingFrame.Position = UDim2.new(0,0,0,0)
loadingFrame.BackgroundColor3 = Color3.fromRGB(20,20,20)
loadingFrame.Parent = screenGui

local loadingText = Instance.new("TextLabel")
loadingText.Size = UDim2.new(1,0,0,50)
loadingText.Position = UDim2.new(0,0,0.5,-25)
loadingText.BackgroundTransparency = 1
loadingText.TextColor3 = Color3.fromRGB(255,255,0)
loadingText.Font = Enum.Font.FredokaOne
loadingText.TextSize = 30
loadingText.Text = "Carregando...\nBenjamim Hub"
loadingText.TextScaled = true
loadingText.Parent = loadingFrame

task.delay(2,function()
    loadingFrame:Destroy()
end)

-- ======== Ícone abrir/fechar Hub ========
local iconButton = Instance.new("TextButton")
iconButton.Size = UDim2.new(0, 50, 0, 50)
iconButton.Position = UDim2.new(0, 20, 0, 20)
iconButton.Text = "☰"
iconButton.Visible = false
iconButton.Parent = screenGui

local iconCorner = Instance.new("UICorner")
iconCorner.CornerRadius = UDim.new(0,10)
iconCorner.Parent = iconButton

task.delay(2,function()
    iconButton.Visible = true
end)

-- ======== Hub ========
local hubFrame = Instance.new("Frame")
hubFrame.Size = UDim2.new(0,300,0,220)
hubFrame.Position = UDim2.new(0.5,-150,0.5,-110)
hubFrame.BackgroundColor3 = Color3.fromRGB(40,40,40)
hubFrame.Visible = false
hubFrame.Parent = screenGui

local hubCorner = Instance.new("UICorner")
hubCorner.CornerRadius = UDim.new(0,15)
hubCorner.Parent = hubFrame

-- Título
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1,0,0,40)
title.Text = "Panel de ADM"
title.TextColor3 = Color3.fromRGB(255,255,255)
title.BackgroundTransparency = 1
title.Font = Enum.Font.SourceSansBold
title.TextSize = 22
title.Parent = hubFrame

-- Créditos
local credit = Instance.new("TextLabel")
credit.Size = UDim2.new(1,0,0,20)
credit.Position = UDim2.new(0,0,0,40)
credit.Text = "Criador: Benjamim   TikTok: Nobizin12"
credit.TextColor3 = Color3.fromRGB(200,200,200)
credit.BackgroundTransparency = 1
credit.Font = Enum.Font.SourceSans
credit.TextSize = 16
credit.Parent = hubFrame

-- ======== Funções Kick e Kill ========
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

-- ======== Botão Kick ========
local kickBtn = Instance.new("TextButton")
kickBtn.Size = UDim2.new(0.8,0,0,40)
kickBtn.Position = UDim2.new(0.1,0,0.35,0)
kickBtn.Text = "Kick Player"
kickBtn.BackgroundColor3 = Color3.fromRGB(200,50,50)
kickBtn.TextColor3 = Color3.fromRGB(255,255,255)
kickBtn.Parent = hubFrame

local kickCorner = Instance.new("UICorner")
kickCorner.CornerRadius = UDim.new(0,10)
kickCorner.Parent = kickBtn

kickBtn.MouseButton1Click:Connect(function()
    local name = Players:GetPlayers()[2] -- Exemplo: 2º player
    if name then
        kickPlayer(name.Name)
    end
end)

-- ======== Botão Kill ========
local killBtn = Instance.new("TextButton")
killBtn.Size = UDim2.new(0.8,0,0,40)
killBtn.Position = UDim2.new(0.1,0,0.6,0)
killBtn.Text = "Kill Player"
killBtn.BackgroundColor3 = Color3.fromRGB(50,50,200)
killBtn.TextColor3 = Color3.fromRGB(255,255,255)
killBtn.Parent = hubFrame

local killCorner = Instance.new("UICorner")
killCorner.CornerRadius = UDim.new(0,10)
killCorner.Parent = killBtn

killBtn.MouseButton1Click:Connect(function()
    local name = Players:GetPlayers()[2] -- Exemplo: 2º player
    if name then
        killPlayer(name.Name)
    end
end)

-- ======== Abrir/Fechar Hub ========
local hubOpen = false
iconButton.MouseButton1Click:Connect(function()
    hubOpen = not hubOpen
    hubFrame.Visible = hubOpen
end)

-- ======== Comandos via chat ========
local function processCommand(player,msg)
    if msg:sub(1,5) == ";kick" then
        local targetName = msg:sub(7)
        kickPlayer(targetName)
    elseif msg:sub(1,5) == ";kill" then
        local targetName = msg:sub(7)
        killPlayer(targetName)
    end
end

Players.PlayerAdded:Connect(function(player)
    player.Chatted:Connect(function(msg)
        processCommand(player,msg)
    end)
end)

LocalPlayer.Chatted:Connect(function(msg)
    processCommand(LocalPlayer,msg)
end)

print("✅ Panel de ADM carregado com sucesso!")
