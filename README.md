--[[
    AGHATA HUB v1.0
    Interface premium estilo cyberpunk neon
    Otimizada para mobile / Delta Executor
    Tamanho: 240x200
]]

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer
local Mouse = LocalPlayer:GetMouse()

-- Configurações da interface
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "AGHATA_HUB"
ScreenGui.ResetOnSpawn = false
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

local MainFrame = Instance.new("Frame")
MainFrame.Size = UDim2.new(0, 240, 0, 200)
MainFrame.Position = UDim2.new(0.5, -120, 0.5, -100)
MainFrame.BackgroundColor3 = Color3.fromRGB(8, 8, 12)
MainFrame.BackgroundTransparency = 0.12
MainFrame.BorderSizePixel = 0
MainFrame.ClipsDescendants = true

-- Corner
local MainCorner = Instance.new("UICorner")
MainCorner.CornerRadius = UDim.new(0, 12)
MainCorner.Parent = MainFrame

-- Glow externo
local GlowFrame = Instance.new("Frame")
GlowFrame.Size = UDim2.new(1, 4, 1, 4)
GlowFrame.Position = UDim2.new(0, -2, 0, -2)
GlowFrame.BackgroundColor3 = Color3.fromRGB(156, 0, 255)
GlowFrame.BackgroundTransparency = 0.85
GlowFrame.BorderSizePixel = 0
GlowFrame.Parent = MainFrame

local GlowCorner = Instance.new("UICorner")
GlowCorner.CornerRadius = UDim.new(0, 14)
GlowCorner.Parent = GlowFrame

-- Outline neon
local Outline = Instance.new("Frame")
Outline.Size = UDim2.new(1, 0, 1, 0)
Outline.BackgroundTransparency = 1
Outline.BorderSizePixel = 1
Outline.BorderColor3 = Color3.fromRGB(156, 0, 255)
Outline.Parent = MainFrame

local OutlineCorner = Instance.new("UICorner")
OutlineCorner.CornerRadius = UDim.new(0, 12)
OutlineCorner.Parent = Outline

-- ============ TOP BAR ============
local TopBar = Instance.new("Frame")
TopBar.Size = UDim2.new(1, 0, 0, 28)
TopBar.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
TopBar.BackgroundTransparency = 0.45
TopBar.BorderSizePixel = 0
TopBar.Parent = MainFrame

local TopCorner = Instance.new("UICorner")
TopCorner.CornerRadius = UDim.new(0, 12)
TopCorner.Parent = TopBar

-- Ícone minimalista roxo
local Icon = Instance.new("Frame")
Icon.Size = UDim2.new(0, 16, 0, 16)
Icon.Position = UDim2.new(0, 8, 0.5, -8)
Icon.BackgroundColor3 = Color3.fromRGB(156, 0, 255)
Icon.BackgroundTransparency = 0.2
Icon.BorderSizePixel = 0
Icon.Parent = TopBar

local IconCorner = Instance.new("UICorner")
IconCorner.CornerRadius = UDim.new(0, 4)
IconCorner.Parent = Icon

local IconGlow = Instance.new("Frame")
IconGlow.Size = UDim2.new(1, 4, 1, 4)
IconGlow.Position = UDim2.new(0, -2, 0, -2)
IconGlow.BackgroundColor3 = Color3.fromRGB(156, 0, 255)
IconGlow.BackgroundTransparency = 0.7
IconGlow.BorderSizePixel = 0
IconGlow.Parent = Icon

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(0, 110, 1, 0)
Title.Position = UDim2.new(0, 28, 0, 0)
Title.BackgroundTransparency = 1
Title.Text = "AGHATA HUB v1.0"
Title.TextColor3 = Color3.fromRGB(220, 220, 255)
Title.TextSize = 11
Title.Font = Enum.Font.GothamBold
Title.TextXAlignment = Enum.TextXAlignment.Left
Title.Parent = TopBar

-- Botão Minimizar
local MinimizeBtn = Instance.new("TextButton")
MinimizeBtn.Size = UDim2.new(0, 24, 0, 20)
MinimizeBtn.Position = UDim2.new(1, -52, 0.5, -10)
MinimizeBtn.BackgroundColor3 = Color3.fromRGB(20, 20, 30)
MinimizeBtn.BackgroundTransparency = 0.5
MinimizeBtn.Text = "—"
MinimizeBtn.TextColor3 = Color3.fromRGB(200, 200, 255)
MinimizeBtn.TextSize = 14
MinimizeBtn.Font = Enum.Font.GothamBold
MinimizeBtn.BorderSizePixel = 0
MinimizeBtn.Parent = TopBar

local MinCorner = Instance.new("UICorner")
MinCorner.CornerRadius = UDim.new(0, 6)
MinCorner.Parent = MinimizeBtn

-- Botão Fechar
local CloseBtn = Instance.new("TextButton")
CloseBtn.Size = UDim2.new(0, 24, 0, 20)
CloseBtn.Position = UDim2.new(1, -26, 0.5, -10)
CloseBtn.BackgroundColor3 = Color3.fromRGB(20, 20, 30)
CloseBtn.BackgroundTransparency = 0.5
CloseBtn.Text = "✕"
CloseBtn.TextColor3 = Color3.fromRGB(255, 80, 120)
CloseBtn.TextSize = 12
CloseBtn.Font = Enum.Font.GothamBold
CloseBtn.BorderSizePixel = 0
CloseBtn.Parent = TopBar

local CloseCorner = Instance.new("UICorner")
CloseCorner.CornerRadius = UDim.new(0, 6)
CloseCorner.Parent = CloseBtn

-- ============ PAINEL PLAYERS (esquerda) ============
local PlayersPanel = Instance.new("Frame")
PlayersPanel.Size = UDim2.new(0, 72, 1, -32)
PlayersPanel.Position = UDim2.new(0, 4, 0, 30)
PlayersPanel.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
PlayersPanel.BackgroundTransparency = 0.4
PlayersPanel.BorderSizePixel = 0
PlayersPanel.Parent = MainFrame

local PlayersCorner = Instance.new("UICorner")
PlayersCorner.CornerRadius = UDim.new(0, 8)
PlayersCorner.Parent = PlayersPanel

local PlayersTitle = Instance.new("TextLabel")
PlayersTitle.Size = UDim2.new(1, 0, 0, 16)
PlayersTitle.BackgroundTransparency = 1
PlayersTitle.Text = "PLAYERS"
PlayersTitle.TextColor3 = Color3.fromRGB(156, 0, 255)
PlayersTitle.TextSize = 9
PlayersTitle.Font = Enum.Font.GothamBold
PlayersTitle.Parent = PlayersPanel

local PlayersList = Instance.new("ScrollingFrame")
PlayersList.Size = UDim2.new(1, -4, 1, -20)
PlayersList.Position = UDim2.new(0, 2, 0, 18)
PlayersList.BackgroundTransparency = 1
PlayersList.BorderSizePixel = 0
PlayersList.ScrollBarThickness = 2
PlayersList.ScrollBarImageColor3 = Color3.fromRGB(156, 0, 255)
PlayersList.CanvasSize = UDim2.new(0, 0, 0, 0)
PlayersList.Parent = PlayersPanel

local PlayersLayout = Instance.new("UIListLayout")
PlayersLayout.Padding = UDim.new(0, 3)
PlayersLayout.SortOrder = Enum.SortOrder.LayoutOrder
PlayersLayout.Parent = PlayersList

-- Função para criar botão de player
local selectedPlayer = nil
local playerButtons = {}

local function createPlayerButton(player)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(1, 0, 0, 22)
    btn.BackgroundColor3 = Color3.fromRGB(15, 15, 22)
    btn.BackgroundTransparency = 0.3
    btn.Text = ""
    btn.BorderSizePixel = 0
    btn.Parent = PlayersList
    
    local btnCorner = Instance.new("UICorner")
    btnCorner.CornerRadius = UDim.new(0, 6)
    btnCorner.Parent = btn
    
    local icon = Instance.new("Frame")
    icon.Size = UDim2.new(0, 12, 0, 12)
    icon.Position = UDim2.new(0, 4, 0.5, -6)
    icon.BackgroundColor3 = Color3.fromRGB(100, 100, 150)
    icon.BackgroundTransparency = 0.5
    icon.BorderSizePixel = 0
    icon.Parent = btn
    
    local iconCorner = Instance.new("UICorner")
    iconCorner.CornerRadius = UDim.new(0, 3)
    iconCorner.Parent = icon
    
    local nameLabel = Instance.new("TextLabel")
    nameLabel.Size = UDim2.new(1, -18, 1, 0)
    nameLabel.Position = UDim2.new(0, 18, 0, 0)
    nameLabel.BackgroundTransparency = 1
    nameLabel.Text = player.Name
    nameLabel.TextColor3 = Color3.fromRGB(200, 200, 220)
    nameLabel.TextSize = 9
    nameLabel.Font = Enum.Font.Gotham
    nameLabel.TextXAlignment = Enum.TextXAlignment.Left
    nameLabel.Parent = btn
    
    btn.MouseButton1Click:Connect(function()
        selectedPlayer = player
        for _, b in pairs(playerButtons) do
            b.BackgroundColor3 = Color3.fromRGB(15, 15, 22)
            b.BackgroundTransparency = 0.3
        end
        btn.BackgroundColor3 = Color3.fromRGB(156, 0, 255)
        btn.BackgroundTransparency = 0.5
    end)
    
    playerButtons[player] = btn
    return btn
end

-- Atualizar lista de players
local function updatePlayersList()
    for _, btn in pairs(playerButtons) do
        btn:Destroy()
    end
    playerButtons = {}
    
    local playerList = Players:GetPlayers()
    for i, player in ipairs(playerList) do
        createPlayerButton(player)
    end
    
    local count = #playerList
    PlayersList.CanvasSize = UDim2.new(0, 0, 0, count * 25 + 5)
end

updatePlayersList()
Players.PlayerAdded:Connect(updatePlayersList)
Players.PlayerRemoving:Connect(updatePlayersList)

-- ============ GRID DE BOTÕES ============
local GridPanel = Instance.new("Frame")
GridPanel.Size = UDim2.new(0, 152, 1, -32)
GridPanel.Position = UDim2.new(0, 80, 0, 30)
GridPanel.BackgroundTransparency = 1
GridPanel.Parent = MainFrame

local GridLayout = Instance.new("UIGridLayout")
GridLayout.CellSize = UDim2.new(0, 46, 0, 28)
GridLayout.CellPadding = UDim2.new(0, 3, 0, 3)
GridLayout.StartCorner = Enum.StartCorner.TopLeft
GridLayout.Parent = GridPanel

-- Função para criar botão neon
local function createNeonButton(name, icon, callback)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(0, 46, 0, 28)
    btn.BackgroundColor3 = Color3.fromRGB(10, 10, 18)
    btn.BackgroundTransparency = 0.2
    btn.Text = ""
    btn.BorderSizePixel = 1
    btn.BorderColor3 = Color3.fromRGB(156, 0, 255)
    btn.Parent = GridPanel
    
    local btnCorner = Instance.new("UICorner")
    btnCorner.CornerRadius = UDim.new(0, 6)
    btnCorner.Parent = btn
    
    local btnGlow = Instance.new("Frame")
    btnGlow.Size = UDim2.new(1, 2, 1, 2)
    btnGlow.Position = UDim2.new(0, -1, 0, -1)
    btnGlow.BackgroundColor3 = Color3.fromRGB(156, 0, 255)
    btnGlow.BackgroundTransparency = 0.9
    btnGlow.BorderSizePixel = 0
    btnGlow.Parent = btn
    
    local btnGlowCorner = Instance.new("UICorner")
    btnGlowCorner.CornerRadius = UDim.new(0, 7)
    btnGlowCorner.Parent = btnGlow
    
    local label = Instance.new("TextLabel")
    label.Size = UDim2.new(1, 0, 1, 0)
    label.BackgroundTransparency = 1
    label.Text = name
    label.TextColor3 = Color3.fromRGB(220, 220, 255)
    label.TextSize = 8
    label.Font = Enum.Font.GothamBold
    label.Parent = btn
    
    btn.MouseButton1Click:Connect(callback)
    
    btn.MouseEnter:Connect(function()
        TweenService:Create(btn, TweenInfo.new(0.15), {BackgroundTransparency = 0.05}):Play()
        TweenService:Create(btnGlow, TweenInfo.new(0.15), {BackgroundTransparency = 0.6}):Play()
    end)
    
    btn.MouseLeave:Connect(function()
        TweenService:Create(btn, TweenInfo.new(0.15), {BackgroundTransparency = 0.2}):Play()
        TweenService:Create(btnGlow, TweenInfo.new(0.15), {BackgroundTransparency = 0.9}):Play()
    end)
    
    return btn
end

-- ============ FUNÇÕES DOS BOTÕES ============

-- Teleport
local teleportActive = false
createNeonButton("TELEPORT", "📍", function()
    teleportActive = not teleportActive
    if teleportActive and Mouse then
        local connection
        connection = Mouse.Button1Down:Connect(function()
            if teleportActive and Mouse.Target then
                local pos = Mouse.Hit.Position
                if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                    LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(pos)
                end
            end
        end)
        task.wait(0.1)
        if not teleportActive then connection:Disconnect() end
    end
end)

-- Visão (Night Vision)
local visionActive = false
createNeonButton("VISÃO", "👁️", function()
    visionActive = not visionActive
    if visionActive then
        local lighting = game:GetService("Lighting")
        lighting.Brightness = 2
        lighting.ClockTime = 12
        lighting.FogEnd = 1000
        lighting.GlobalShadows = false
        lighting.OutdoorAmbient = Color3.fromRGB(128, 128, 255)
    else
        local lighting = game:GetService("Lighting")
        lighting.Brightness = 1
        lighting.FogEnd = 400
        lighting.GlobalShadows = true
        lighting.OutdoorAmbient = Color3.fromRGB(127, 127, 127)
    end
end)

-- Puxar (Pull)
local pullActive = false
createNeonButton("PUXAR", "🔄", function()
    pullActive = not pullActive
    if pullActive and selectedPlayer and selectedPlayer.Character then
        local targetHRP = selectedPlayer.Character:FindFirstChild("HumanoidRootPart")
        local localHRP = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
        if targetHRP and localHRP then
            targetHRP.CFrame = localHRP.CFrame + Vector3.new(0, 2, 0)
        end
    end
end)

-- Noclip
local noclipActive = false
local noclipConn
createNeonButton("NOCLIP", "🚪", function()
    noclipActive = not noclipActive
    if noclipActive then
        noclipConn = RunService.Stepped:Connect(function()
            if LocalPlayer.Character then
                for _, part in pairs(LocalPlayer.Character:GetDescendants()) do
                    if part:IsA("BasePart") then
                        part.CanCollide = false
                    end
                end
            end
        end)
    else
        if noclipConn then noclipConn:Disconnect() end
        if LocalPlayer.Character then
            for _, part in pairs(LocalPlayer.Character:GetDescendants()) do
                if part:IsA("BasePart") then
                    part.CanCollide = true
                end
            end
        end
    end
end)

-- Hitbox
local hitboxSize = 5
local hitboxActive = false
createNeonButton("HITBOX", "🎯", function()
    hitboxActive = not hitboxActive
    if hitboxActive then
        local function enlargeHitbox()
            if LocalPlayer.Character then
                for _, part in pairs(LocalPlayer.Character:GetChildren()) do
                    if part:IsA("BasePart") and part.Name ~= "HumanoidRootPart" then
                        part.Size = Vector3.new(hitboxSize, hitboxSize, hitboxSize)
                    end
                end
            end
        end
        enlargeHitbox()
        task.spawn(function()
            while hitboxActive do
                enlargeHitbox()
                task.wait(0.5)
            end
        end)
    else
        if LocalPlayer.Character then
            for _, part in pairs(LocalPlayer.Character:GetChildren()) do
                if part:IsA("BasePart") and part.Name ~= "HumanoidRootPart" then
                    part.Size = Vector3.new(2, 2, 1)
                end
            end
        end
    end
end)

-- Invisível
local invisibleActive = false
createNeonButton("INVISÍVEL", "👻", function()
    invisibleActive = not invisibleActive
    if LocalPlayer.Character then
        for _, part in pairs(LocalPlayer.Character:GetChildren()) do
            if part:IsA("BasePart") then
                part.Transparency = invisibleActive and 0.9 or 0
            end
        end
        if LocalPlayer.Character:FindFirstChild("Head") then
            LocalPlayer.Character.Head.Transparency = invisibleActive and 0.9 or 0
        end
    end
end)

-- Super Pulo
local superJumpActive = false
local originalJumpPower = 50
createNeonButton("SUPER\nPULO", "🦘", function()
    superJumpActive = not superJumpActive
    if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
        local humanoid = LocalPlayer.Character.Humanoid
        if superJumpActive then
            originalJumpPower = humanoid.JumpPower
            humanoid.JumpPower = 150
        else
            humanoid.JumpPower = originalJumpPower
        end
    end
end)

-- Telecinesia
local telekinesisActive = false
local heldPart = nil
createNeonButton("TELECINESIA", "🌀", function()
    telekinesisActive = not telekinesisActive
    if telekinesisActive then
        local connection
        connection = Mouse.Button1Down:Connect(function()
            if telekinesisActive and Mouse.Target and Mouse.Target:IsA("BasePart") then
                heldPart = Mouse.Target
                local grabConn
                grabConn = RunService.RenderStepped:Connect(function()
                    if heldPart and telekinesisActive then
                        heldPart.CFrame = CFrame.new(Mouse.Hit.Position)
                    end
                end)
                task.wait()
                if not telekinesisActive then grabConn:Disconnect() end
            end
        end)
    else
        heldPart = nil
    end
end)

-- Aura
local auraActive = false
local auraPart = nil
createNeonButton("AURA", "✨", function()
    auraActive = not auraActive
    if auraActive then
        auraPart = Instance.new("Part")
        auraPart.Size = Vector3.new(6, 6, 6)
        auraPart.Shape = Enum.PartType.Ball
        auraPart.BrickColor = BrickColor.new("Bright violet")
        auraPart.Material = Enum.Material.Neon
        auraPart.Transparency = 0.7
        auraPart.Anchored = true
        auraPart.CanCollide = false
        auraPart.Parent = workspace
        
        local attachConn = RunService.RenderStepped:Connect(function()
            if auraActive and LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                auraPart.CFrame = LocalPlayer.Character.HumanoidRootPart.CFrame
            elseif auraPart then
                auraPart:Destroy()
            end
        end)
    else
        if auraPart then auraPart:Destroy() end
    end
end)

-- ============ CONTROLE HITBOX ============
local HitboxControl = Instance.new("Frame")
HitboxControl.Size = UDim2.new(0, 46, 0, 28)
HitboxControl.Position = UDim2.new(0, 98, 0, 164)
HitboxControl.BackgroundColor3 = Color3.fromRGB(10, 10, 18)
HitboxControl.BackgroundTransparency = 0.2
HitboxControl.BorderSizePixel = 1
HitboxControl.BorderColor3 = Color3.fromRGB(156, 0, 255)
HitboxControl.Parent = GridPanel

local HitboxCorner = Instance.new("UICorner")
HitboxCorner.CornerRadius = UDim.new(0, 6)
HitboxCorner.Parent = HitboxControl

local HitboxLabel = Instance.new("TextLabel")
HitboxLabel.Size = UDim2.new(1, 0, 0, 12)
HitboxLabel.Position = UDim2.new(0, 0, 0, 2)
HitboxLabel.BackgroundTransparency = 1
HitboxLabel.Text = "HITBOX"
HitboxLabel.TextColor3 = Color3.fromRGB(156, 0, 255)
HitboxLabel.TextSize = 7
HitboxLabel.Font = Enum.Font.GothamBold
HitboxLabel.Parent = HitboxControl

local HitboxValue = Instance.new("TextLabel")
HitboxValue.Size = UDim2.new(1, -20, 0, 12)
HitboxValue.Position = UDim2.new(0, 0, 0, 14)
HitboxValue.BackgroundTransparency = 1
HitboxValue.Text = tostring(hitboxSize)
HitboxValue.TextColor3 = Color3.fromRGB(220, 220, 255)
HitboxValue.TextSize = 9
HitboxValue.Font = Enum.Font.GothamBold
HitboxValue.Parent = HitboxControl

local MinusBtn = Instance.new("TextButton")
MinusBtn.Size = UDim2.new(0, 14, 0, 12)
MinusBtn.Position = UDim2.new(1, -14, 0, 14)
MinusBtn.BackgroundColor3 = Color3.fromRGB(156, 0, 255)
MinusBtn.BackgroundTransparency = 0.4
MinusBtn.Text = "-"
MinusBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
MinusBtn.TextSize = 10
MinusBtn.Font = Enum.Font.GothamBold
MinusBtn.BorderSizePixel = 0
MinusBtn.Parent = HitboxControl

local MinusCorner = Instance.new("UICorner")
MinusCorner.CornerRadius = UDim.new(0, 3)
MinusCorner.Parent = MinusBtn

local PlusBtn = Instance.new("TextButton")
PlusBtn.Size = UDim2.new(0, 14, 0, 12)
PlusBtn.Position = UDim2.new(1, -30, 0, 14)
PlusBtn.BackgroundColor3 = Color3.fromRGB(156, 0, 255)
PlusBtn.BackgroundTransparency = 0.4
PlusBtn.Text = "+"
PlusBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
PlusBtn.TextSize = 10
PlusBtn.Font = Enum.Font.GothamBold
PlusBtn.BorderSizePixel = 0
PlusBtn.Parent = HitboxControl

local PlusCorner = Instance.new("UICorner")
PlusCorner.CornerRadius = UDim.new(0, 3)
PlusCorner.Parent = PlusBtn

MinusBtn.MouseButton1Click:Connect(function()
    hitboxSize = math.max(1, hitboxSize - 1)
    HitboxValue.Text = tostring(hitboxSize)
    if hitboxActive then
        if LocalPlayer.Character then
            for _, part in pairs(LocalPlayer.Character:GetChildren()) do
                if part:IsA("BasePart") and part.Name ~= "HumanoidRootPart" then
                    part.Size = Vector3.new(hitboxSize, hitboxSize, hitboxSize)
                end
            end
        end
    end
end)

PlusBtn.MouseButton1Click:Connect(function()
    hitboxSize = math.min(12, hitboxSize + 1)
    HitboxValue.Text = tostring(hitboxSize)
    if hitboxActive then
        if LocalPlayer.Character then
            for _, part in pairs(LocalPlayer.Character:GetChildren()) do
                if part:IsA("BasePart") and part.Name ~= "HumanoidRootPart" then
                    part.Size = Vector3.new(hitboxSize, hitboxSize, hitboxSize)
                end
            end
        end
    end
end)

-- ============ HP À DISTÂNCIA ============
local HpPanel = Instance.new("Frame")
HpPanel.Size = UDim2.new(0, 50, 0, 36)
HpPanel.Position = UDim2.new(0, 180, 0, 164)
HpPanel.BackgroundColor3 = Color3.fromRGB(10, 10, 18)
HpPanel.BackgroundTransparency = 0.2
HpPanel.BorderSizePixel = 1
HpPanel.BorderColor3 = Color3.fromRGB(156, 0, 255)
HpPanel.Parent = MainFrame

local HpCorner = Instance.new("UICorner")
HpCorner.CornerRadius = UDim.new(0, 6)
HpCorner.Parent = HpPanel

local HpTitle = Instance.new("TextLabel")
HpTitle.Size = UDim2.new(1, 0, 0, 10)
HpTitle.BackgroundTransparency = 1
HpTitle.Text = "HP à distância"
HpTitle.TextColor3 = Color3.fromRGB(156, 0, 255)
HpTitle.TextSize = 6
HpTitle.Font = Enum.Font.GothamBold
HpTitle.Parent = HpPanel

-- Boneco minimalista
local Stickman = Instance.new("Frame")
Stickman.Size = UDim2.new(0, 30, 0, 18)
Stickman.Position = UDim2.new(0.5, -15, 0, 12)
Stickman.BackgroundTransparency = 1
Stickman.Parent = HpPanel

local Body = Instance.new("Frame")
Body.Size = UDim2.new(0, 8, 0, 10)
Body.Position = UDim2.new(0.5, -4, 0, 4)
Body.BackgroundColor3 = Color3.fromRGB(200, 200, 255)
Body.BackgroundTransparency = 0.3
Body.BorderSizePixel = 0
Body.Parent = Stickman

local Head = Instance.new("Frame")
Head.Size = UDim2.new(0, 6, 0, 6)
Head.Position = UDim2.new(0.5, -3, 0, 0)
Head.BackgroundColor3 = Color3.fromRGB(200, 200, 255)
Head.BackgroundTransparency = 0.3
Head.BorderSizePixel = 0
Head.Parent = Stickman

local HeadCorner = Instance.new("UICorner")
HeadCorner.CornerRadius = UDim.new(1, 0)
HeadCorner.Parent = Head

local HealthBar = Instance.new("Frame")
HealthBar.Size = UDim2.new(0, 20, 0, 2)
HealthBar.Position = UDim2.new(0.5, -10, 0, 16)
HealthBar.BackgroundColor3 = Color3.fromRGB(0, 255, 100)
HealthBar.BorderSizePixel = 0
HealthBar.Parent = Stickman

local HealthBarBg = Instance.new("Frame")
HealthBarBg.Size = UDim2.new(0, 20, 0, 2)
HealthBarBg.Position = UDim2.new(0.5, -10, 0, 16)
HealthBarBg.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
HealthBarBg.BorderSizePixel = 0
HealthBarBg.Parent = Stickman

HealthBarBg.ZIndex = 0
HealthBar.ZIndex = 1

-- ============ INFORMAÇÕES ============
local InfoPanel = Instance.new("Frame")
InfoPanel.Size = UDim2.new(1, -8, 0, 32)
InfoPanel.Position = UDim2.new(0, 4, 1, -36)
InfoPanel.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
InfoPanel.BackgroundTransparency = 0.5
InfoPanel.BorderSizePixel = 0
InfoPanel.Parent = MainFrame

local InfoCorner = Instance.new("UICorner")
InfoCorner.CornerRadius = UDim.new(0, 8)
InfoCorner.Parent = InfoPanel

-- Linha divisória neon
local Divider = Instance.new("Frame")
Divider.Size = UDim2.new(1, -16, 0, 1)
Divider.Position = UDim2.new(0, 8, 0.5, -0.5)
Divider.BackgroundColor3 = Color3.fromRGB(156, 0, 255)
Divider.BackgroundTransparency = 0.5
Divider.BorderSizePixel = 0
Divider.Parent = InfoPanel

-- Informações
local infoValues = {
    Vida = Instance.new("TextLabel"),
    Status = Instance.new("TextLabel"),
    Ping = Instance.new("TextLabel"),
    Velocidade = Instance.new("TextLabel")
}

local xPos = 6
for i, (name, label) in pairs(infoValues) do
    label.Size = UDim2.new(0, 52, 1, 0)
    label.Position = UDim2.new(0, xPos, 0, 0)
    label.BackgroundTransparency = 1
    label.Text = name .. ": --"
    label.TextColor3 = Color3.fromRGB(180, 180, 220)
    label.TextSize = 8
    label.Font = Enum.Font.Gotham
    label.TextXAlignment = Enum.TextXAlignment.Left
    label.Parent = InfoPanel
    xPos = xPos + 54
end

infoValues.Vida.Text = "VIDA: 100/100"
infoValues.Status.Text = "STATUS: ATIVO"
infoValues.Ping.Text = "PING: 0ms"
infoValues.Velocidade.Text = "VEL: 16"

-- Atualizar informações
task.spawn(function()
    while true do
        task.wait(0.5)
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
            local humanoid = LocalPlayer.Character.Humanoid
            infoValues.Vida.Text = string.format("VIDA: %d/100", math.floor(humanoid.Health))
        end
        
        local ping = game:GetService("Stats"):FindFirstChild("Network") and game:GetService("Stats").Network:FindFirstChild("Ping")
        if ping then
            infoValues.Ping.Text = "PING: " .. math.floor(ping.Value) .. "ms"
        end
        
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            local vel = LocalPlayer.Character.HumanoidRootPart.Velocity.Magnitude
            infoValues.Velocidade.Text = "VEL: " .. math.floor(vel)
        end
        
        -- Atualizar barra de HP do boneco
        if selectedPlayer and selectedPlayer.Character and selectedPlayer.Character:FindFirstChild("Humanoid") then
            local hpPercent = selectedPlayer.Character.Humanoid.Health / selectedPlayer.Character.Humanoid.MaxHealth
            HealthBar.Size = UDim2.new(0, 20 * hpPercent, 0, 2)
            HealthBar.BackgroundColor3 = Color3.fromRGB(0, 255, 100)
        else
            HealthBar.Size = UDim2.new(0, 20, 0, 2)
        end
    end
end)

-- ============ LOGO ============
local Logo = Instance.new("TextLabel")
Logo.Size = UDim2.new(0, 40, 0, 16)
Logo.Position = UDim2.new(1, -44, 1, -32)
Logo.BackgroundTransparency = 1
Logo.Text = "⍟"
Logo.TextColor3 = Color3.fromRGB(156, 0, 255)
Logo.TextSize = 18
Logo.Font = Enum.Font.GothamBold
Logo.TextXAlignment = Enum.TextXAlignment.Right
Logo.Parent = MainFrame

-- ============ DRAG SYSTEM ============
local dragging = false
local dragStart, startPos

MainFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1 then
        if input.Position.Y - MainFrame.AbsolutePosition.Y <= 28 then
            dragging = true
            dragStart = input.Position
            startPos = MainFrame.Position
        end
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if dragging and (input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseMovement) then
        local delta = input.Position - dragStart
        MainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)

UserInputService.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = false
    end
end)

-- ============ MINIMIZAR / FECHAR ============
local minimized = false
MinimizeBtn.MouseButton1Click:Connect(function()
    minimized = not minimized
    MainFrame.Size = minimized and UDim2.new(0, 240, 0, 28) or UDim2.new(0, 240, 0, 200)
    for _, child in pairs(MainFrame:GetChildren()) do
        if child ~= TopBar and child ~= MinimizeBtn and child ~= CloseBtn and child ~= Outline and child ~= GlowFrame then
            child.Visible = not minimized
        end
    end
end)

CloseBtn.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

-- Finalizar
ScreenGui.Parent = game:GetService("CoreGui")
MainFrame.Parent = ScreenGui

-- Mensagem de sucesso
local notif = Instance.new("TextLabel")
notif.Size = UDim2.new(0, 160, 0, 30)
notif.Position = UDim2.new(0.5, -80, 0, 50)
notif.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
notif.BackgroundTransparency = 0.3
notif.Text = "AGHATA HUB v1.0 CARREGADO"
notif.TextColor3 = Color3.fromRGB(156, 0, 255)
notif.TextSize = 11
notif.Font = Enum.Font.GothamBold
notif.Parent = ScreenGui

local notifCorner = Instance.new("UICorner")
notifCorner.CornerRadius = UDim.new(0, 8)
notifCorner.Parent = notif

task.wait(2)
notif:Destroy()
