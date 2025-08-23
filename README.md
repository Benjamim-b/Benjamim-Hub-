--// Script Hub Moderno
-- Criador: Benjamim | TikTok: Nobizin12
-- Suba esse código no GitHub e rode via loadstring

local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- ScreenGui principal
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "ScriptHub"
screenGui.Parent = playerGui
screenGui.ResetOnSpawn = false

-- Ícone de abrir/fechar
local icon = Instance.new("TextButton")
icon.Name = "OpenCloseIcon"
icon.Size = UDim2.new(0, 120, 0, 40)
icon.Position = UDim2.new(0, 20, 0, 200)
icon.Text = "📜 Script Hub"
icon.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
icon.TextColor3 = Color3.fromRGB(255,255,255)
icon.Parent = screenGui

local uicorner = Instance.new("UICorner")
uicorner.CornerRadius = UDim.new(0,10)
uicorner.Parent = icon

-- Frame do Hub
local hub = Instance.new("Frame")
hub.Name = "HubMain"
hub.Size = UDim2.new(0, 400, 0, 450)
hub.Position = UDim2.new(0.5, -200, 0.5, -225)
hub.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
hub.Visible = false
hub.Parent = screenGui

local hubCorner = Instance.new("UICorner")
hubCorner.CornerRadius = UDim.new(0,12)
hubCorner.Parent = hub

-- Título
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1,0,0,40)
title.Text = "Script Hub - Criador: Benjamim | TikTok: Nobizin12"
title.BackgroundTransparency = 1
title.TextColor3 = Color3.fromRGB(255,255,0)
title.Font = Enum.Font.SourceSansBold
title.TextSize = 18
title.Parent = hub

-- Permitir mover
local dragging, dragInput, dragStart, startPos
local UIS = game:GetService("UserInputService")

local function update(input)
	local delta = input.Position - dragStart
	hub.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X,
		startPos.Y.Scale, startPos.Y.Offset + delta.Y)
end

hub.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 then
		dragging = true
		dragStart = input.Position
		startPos = hub.Position

		input.Changed:Connect(function()
			if input.UserInputState == Enum.UserInputState.End then
				dragging = false
			end
		end)
	end
end)

hub.InputChanged:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseMovement then
		dragInput = input
	end
end)

UIS.InputChanged:Connect(function(input)
	if input == dragInput and dragging then
		update(input)
	end
end)

-- Abrir/fechar Hub
icon.MouseButton1Click:Connect(function()
	hub.Visible = not hub.Visible
end)

-- Função utilitária para criar botões
local function createButton(name, yPos)
	local btn = Instance.new("TextButton")
	btn.Size = UDim2.new(1, -20, 0, 35)
	btn.Position = UDim2.new(0, 10, 0, yPos)
	btn.Text = name
	btn.BackgroundColor3 = Color3.fromRGB(45,45,45)
	btn.TextColor3 = Color3.fromRGB(255,255,255)
	btn.Parent = hub
	local c = Instance.new("UICorner", btn)
	c.CornerRadius = UDim.new(0,8)
	return btn
end

-- Criando os 10 botões
local btn1 = createButton("1 - Créditos", 50)
local btn2 = createButton("2 - Troll", 90)
local btn3 = createButton("3 - Chat Premium", 130)
local btn4 = createButton("4 - Copiador de Avatar", 170)
local btn5 = createButton("5 - Fun (Premium / Vip)", 210)
local btn6 = createButton("6 - Configurações", 250)
local btn7 = createButton("7 - View", 290)
local btn8 = createButton("8 - Chat Troll Visual", 330)
local btn9 = createButton("9 - Outros Scripts", 370)
local btn10 = createButton("10 - Misc (GamePass)", 410)

--// AÇÕES DOS BOTÕES (placeholders)
btn1.MouseButton1Click:Connect(function()
	game:GetService("StarterGui"):SetCore("SendNotification", {
		Title = "Créditos";
		Text = "Servidor: discord.gg/NXtJAPAg\nExecutor: "..player.Name;
		Duration = 6;
	})
end)

btn2.MouseButton1Click:Connect(function()
	print("Troll menu seria aberto aqui (Bring, Bring V2, Bola V2 etc.)")
end)

btn3.MouseButton1Click:Connect(function()
	print("Chat Premium ativado para "..player.Name)
end)

btn4.MouseButton1Click:Connect(function()
	print("Copiador de Avatar ativado")
end)

btn5.MouseButton1Click:Connect(function()
	print("Premium/Vip concedido")
end)

btn6.MouseButton1Click:Connect(function()
	print("Abrir configurações de cor e salvar")
end)

btn7.MouseButton1Click:Connect(function()
	print("View ativado")
end)

btn8.MouseButton1Click:Connect(function()
	print("Chat Troll Visual ativado")
end)

btn9.MouseButton1Click:Connect(function()
	print("Executar scripts externos (Coquette Hub, Lolyta, davi999 etc.)")
end)

btn10.MouseButton1Click:Connect(function()
	print("Misc: GamePass Brookhaven ativado")
end)
