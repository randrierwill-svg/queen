-- Painel Open Source estilo "Steal a Brainrot"
-- Autor: você pode citar como quiser
-- Coloque em StarterGui > LocalScript

-- Criar o ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "BrainrotPanel"
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Criar o Painel da Esquerda
local leftFrame = Instance.new("Frame")
leftFrame.Size = UDim2.new(0, 200, 0, 300)
leftFrame.Position = UDim2.new(0.05, 0, 0.3, 0)
leftFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
leftFrame.BorderSizePixel = 2
leftFrame.Parent = screenGui

-- Título
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 40)
title.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
title.Text = "MIRANDA TWEEN"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Font = Enum.Font.SourceSansBold
title.TextSize = 20
title.Parent = leftFrame

-- Função para criar botões
local function createButton(parent, name, yPos, callback)
    local button = Instance.new("TextButton")
    button.Size = UDim2.new(0.9, 0, 0, 40)
    button.Position = UDim2.new(0.05, 0, 0, yPos)
    button.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
    button.Text = name
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.Font = Enum.Font.SourceSansBold
    button.TextSize = 16
    button.Parent = parent

    button.MouseButton1Click:Connect(function()
        print(name .. " clicado!")
        if callback then callback() end
    end)

    return button
end

-- Criar botões da esquerda
createButton(leftFrame, "ESP GOD", 50)
createButton(leftFrame, "ESP SECRET", 100)
createButton(leftFrame, "ESP BASE", 150)
createButton(leftFrame, "ESP PLAYER", 200)

-- Painel da direita (inicialmente escondido)
local rightFrame = Instance.new("Frame")
rightFrame.Size = UDim2.new(0, 200, 0, 200)
rightFrame.Position = UDim2.new(0.25, 0, 0.3, 0)
rightFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
rightFrame.BorderSizePixel = 2
rightFrame.Visible = false
rightFrame.Parent = screenGui

local rightTitle = Instance.new("TextLabel")
rightTitle.Size = UDim2.new(1, 0, 0, 40)
rightTitle.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
rightTitle.Text = "INSTANT STEAL"
rightTitle.TextColor3 = Color3.fromRGB(255, 255, 255)
rightTitle.Font = Enum.Font.SourceSansBold
rightTitle.TextSize = 20
rightTitle.Parent = rightFrame

-- Botões do painel da direita
createButton(rightFrame, "Instant Steal", 50)
createButton(rightFrame, "Aimbot Teia", 100)
createButton(rightFrame, "AUTO KICK", 150)

-- Botão especial que abre o painel da direita
createButton(leftFrame, "Miranda Insta Steal", 250, function()
    rightFrame.Visible = not rightFrame.Visible
end)
