--// Hub Completo com Loadstring
-- Salve este script no seu GitHub e rode com:
-- loadstring(game:HttpGet("https://raw.githubusercontent.com/SEU-USUARIO/SEU-REPOSITORIO/main/HubScript.lua"))()

local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "ScriptHub"
screenGui.Parent = playerGui

-- Ícone abrir/fechar
local iconButton = Instance.new("TextButton")
iconButton.Name = "Icon"
iconButton.Text = "📜 Script Hub"
iconButton.Size = UDim2.new(0, 120, 0, 40)
iconButton.Position = UDim2.new(0.05, 0, 0.1, 0)
iconButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
iconButton.TextColor3 = Color3.fromRGB(255, 255, 255)
iconButton.Parent = screenGui

local uiCorner = Instance.new("UICorner")
uiCorner.CornerRadius = UDim.new(0, 12)
uiCorner.Parent = iconButton

-- Frame principal
local hubFrame = Instance.new("Frame")
hubFrame.Size = UDim2.new(0, 500, 0, 400)
hubFrame.Position = UDim2.new(0.25, 0, 0.2, 0)
hubFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
hubFrame.Visible = false
hubFrame.Parent = screenGui

local hubCorner = Instance.new("UICorner")
hubCorner.CornerRadius = UDim.new(0, 15)
hubCorner.Parent = hubFrame

-- Título
local title = Instance.new("TextLabel")
title.Text = "Script Hub\nCriador: Benjamim | Tiktok: Nobizin12"
title.Size = UDim2.new(1, 0, 0, 60)
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.BackgroundTransparency = 1
title.Font = Enum.Font.SourceSansBold
title.TextSize = 22
title.Parent = hubFrame

-- Função arrastar
local UIS = game:GetService("UserInputService")
local dragging, dragInput, dragStart, startPos

local function update(input)
	local delta = input.Position - dragStart
	hubFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
end

iconButton.MouseButton1Down:Connect(function()
	hubFrame.Visible = not hubFrame.Visible
end)

hubFrame.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 then
		dragging = true
		dragStart = input.Position
		startPos = hubFrame.Position

		input.Changed:Connect(function()
			if input.UserInputState == Enum.UserInputState.End then
				dragging = false
			end
		end)
	end
end)

hubFrame.InputChanged:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseMovement then
		dragInput = input
	end
end)

UIS.InputChanged:Connect(function(input)
	if input == dragInput and dragging then
		update(input)
	end
end)

-- Criar botões
local function createButton(name, yPos, callback)
	local button = Instance.new("TextButton")
	button.Text = name
	button.Size = UDim2.new(0.9, 0, 0, 35)
	button.Position = UDim2.new(0.05, 0, 0, yPos)
	button.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
	button.TextColor3 = Color3.fromRGB(255, 255, 255)
	button.Parent = hubFrame

	local btnCorner = Instance.new("UICorner")
	btnCorner.CornerRadius = UDim.new(0, 10)
	btnCorner.Parent = button

	button.MouseButton1Click:Connect(callback)
	return button
end

-- Botões com funções placeholder (você ajusta depois)
createButton("1. Créditos", 70, function()
	print("Abrindo créditos... Discord: https://discord.gg/NXtJAPAg")
end)

createButton("2. Troll (Bring, Bola, Void)", 110, function()
	print("Executando Troll Commands...")
end)

createButton("3. Chat Premium", 150, function()
	print("Chat Premium ativado!")
end)

createButton("4. Copiador de Avatar", 190, function()
	print("Copiando avatar...")
end)

createButton("5. Fun (Premium/Vip)", 230, function()
	print("Dando Premium/Vip...")
end)

createButton("6. Configuração (Cor + Salvar)", 270, function()
	print("Abrindo Configuração...")
end)

createButton("7. View", 310, function()
	print("View ativado...")
end)

createButton("8. Chat Troll Visual", 350, function()
	print("Chat troll ligado...")
end)

createButton("9. Scripts Parceiros", 390, function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/davi999/coquette/main/hub.lua"))()
end)

createButton("10. Misc (Gamepass Brookhaven)", 430, function()
	print("Gamepasses liberados...")
end)
