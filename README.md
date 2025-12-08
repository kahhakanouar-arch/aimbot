-- Pablex77 Hub + Key System (ESP Name/HP + Wallcheck + FOV Fixe) - ANOUAR IS THE KING
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local Camera = workspace.CurrentCamera
local Player = Players.LocalPlayer

-- === KEY SYSTEM ===
local CorrectKey = "anouar777x"
local MaxAttempts = 3
local Attempts = 0

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "KING IS ANOUAR"
ScreenGui.Parent = game.CoreGui
ScreenGui.IgnoreGuiInset = true

-- Key GUI (inchangé)
local KeyFrame = Instance.new("Frame")
KeyFrame.Size = UDim2.new(0, 350, 0, 200)
KeyFrame.Position = UDim2.new(0.5, -175, 0.5, -100)
KeyFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
KeyFrame.BorderSizePixel = 0
KeyFrame.Parent = ScreenGui
Instance.new("UICorner", KeyFrame).CornerRadius = UDim.new(0, 12)

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, 0, 0.3, 0)
Title.BackgroundTransparency = 1
Title.Text = "ANOUAR IS THE KING - Key System"
Title.TextColor3 = Color3.fromRGB(255, 0, 0)
Title.TextScaled = true
Title.Font = Enum.Font.GothamBold
Title.Parent = KeyFrame

local KeyBox = Instance.new("TextBox")
KeyBox.Size = UDim2.new(0.8, 0, 0.25, 0)
KeyBox.Position = UDim2.new(0.1, 0, 0.35, 0)
KeyBox.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
KeyBox.PlaceholderText = "Enter your key here..."
KeyBox.TextColor3 = Color3.fromRGB(255, 0, 0)
KeyBox.TextScaled = true
KeyBox.Parent = KeyFrame
Instance.new("UICorner", KeyBox).CornerRadius = UDim.new(0, 8)

local ValidateBtn = Instance.new("TextButton")
ValidateBtn.Size = UDim2.new(0.8, 0, 0.2, 0)
ValidateBtn.Position = UDim2.new(0.1, 0, 0.7, 0)
ValidateBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
ValidateBtn.Text = "Validate Key"
ValidateBtn.TextColor3 = Color3.new(0,0,0)
ValidateBtn.TextScaled = true
ValidateBtn.Parent = KeyFrame
Instance.new("UICorner", ValidateBtn).CornerRadius = UDim.new(0, 8)

local StatusLabel = Instance.new("TextLabel")
StatusLabel.Size = UDim2.new(0.9, 0, 0.15, 0)
StatusLabel.Position = UDim2.new(0.05, 0, 0.55, 0)
StatusLabel.BackgroundTransparency = 1
StatusLabel.Text = "Enter key and click Validate"
StatusLabel.TextColor3 = Color3.new(1,1,1)
StatusLabel.TextScaled = true
StatusLabel.Parent = KeyFrame

ValidateBtn.MouseButton1Click:Connect(function()
    if Attempts >= MaxAttempts then Player:Kick("Too many attempts!") return end
    if KeyBox.Text == CorrectKey then
        StatusLabel.Text = "Key accepted! Loading..."
        StatusLabel.TextColor3 = Color3.fromRGB(0, 255, 0)
        wait(1.5)
        KeyFrame:Destroy()
        LoadMainGUI()
    else
        Attempts += 1
        StatusLabel.Text = "Wrong key! ("..(MaxAttempts-Attempts).." left)"
        StatusLabel.TextColor3 = Color3.fromRGB(255, 0, 0)
        KeyBox.Text = ""
    end
end)

function LoadMainGUI()
    -- GUI (identique)
    local MainFrame = Instance.new("Frame")
    MainFrame.Size = UDim2.new(0.4, 0, 0.5, 0)
    MainFrame.Position = UDim2.new(0.3, 0, 0.25, 0)
    MainFrame.BackgroundColor3 = Color3.new(0,0,0)
    MainFrame.Visible = false
    MainFrame.Parent = ScreenGui
    Instance.new("UICorner", MainFrame).CornerRadius = UDim.new(0, 8)

    local MainDrag = Instance.new("Frame")
    MainDrag.Size = UDim2.new(1,0,0.1,0)
    MainDrag.BackgroundTransparency = 1
    MainDrag.Parent = MainFrame

    local ToggleButton = Instance.new("TextButton")
    ToggleButton.Size = UDim2.new(0, 100, 0, 40)
    ToggleButton.Position = UDim2.new(0.9, 0, 0.05, 0)
    ToggleButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
    ToggleButton.Text = "Open"
    ToggleButton.TextScaled = true
    ToggleButton.Parent = ScreenGui
    Instance.new("UICorner", ToggleButton).CornerRadius = UDim.new(0, 8)

    local ToggleDrag = Instance.new("Frame")
    ToggleDrag.Size = UDim2.new(1,0,1,0)
    ToggleDrag.BackgroundTransparency = 1
    ToggleDrag.Parent = ToggleButton

    local ESPToggle = Instance.new("TextButton")
    ESPToggle.Size = UDim2.new(0.8,0,0.2,0)
    ESPToggle.Position = UDim2.new(0.1,0,0.1,0)
    ESPToggle.BackgroundColor3 = Color3.fromRGB(255,0,0)
    ESPToggle.Text = "ESP: OFF"
    ESPToggle.TextScaled = true
    ESPToggle.Parent = MainFrame
    Instance.new("UICorner", ESPToggle).CornerRadius = UDim.new(0,8)

    local AimbotToggle = Instance.new("TextButton")
    AimbotToggle.Size = UDim2.new(0.8,0,0.2,0)
    AimbotToggle.Position = UDim2.new(0.1,0,0.35,0)
    AimbotToggle.BackgroundColor3 = Color3.fromRGB(255,0,0)
    AimbotToggle.Text = "Aimbot: OFF"
    AimbotToggle.TextScaled = true
    AimbotToggle.Parent = MainFrame
    Instance.new("UICorner", AimbotToggle).CornerRadius = UDim.new(0,8)

    local FOVSlider = Instance.new("TextBox")
    FOVSlider.Size = UDim2.new(0.8,0,0.2,0)
    FOVSlider.Position = UDim2.new(0.1,0,0.6,0)
    FOVSlider.BackgroundColor3 = Color3.fromRGB(50,50,50)
    FOVSlider.Text = "FOV: 80"
    FOVSlider.TextColor3 = Color3.fromRGB(255,0,0)
    FOVSlider.TextScaled = true
    FOVSlider.Parent = MainFrame
    Instance.new("UICorner", FOVSlider).CornerRadius = UDim.new(0,8)

    -- Variables
    local espEnabled = false
    local AimbotOn = false
    local FOVRadius = 80
    local AimPart = "Head"

    local FOVCircle = Drawing.new("Circle")
    FOVCircle.Radius = FOVRadius
    FOVCircle.Thickness = 2
    FOVCircle.Color = Color3.fromRGB(255,0,0)
    FOVCircle.Transparency = 0.6
    FOVCircle.Filled = false
    FOVCircle.Visible = false

    -- === WALLCHECK FUNCTION ===
    local function isVisible(targetPart)
        local origin = Camera.CFrame.Position
        local direction = (targetPart.Position - origin)
        local rayParams = RaycastParams.new()
        rayParams.FilterDescendantsInstances = {Player.Character or Player.CharacterAdded:Wait()}
        rayParams.FilterType = Enum.RaycastFilterType.Blacklist
        local result = workspace:Raycast(origin, direction, rayParams)
        return result == nil or result.Instance:IsDescendantOf(targetPart.Parent)
    end

    -- === ESP NAME + HP VERT FIXE (INSTANTANÉ) ===
    local function createNameESP(char)
        local plr = Players:GetPlayerFromCharacter(char)
        if not plr or plr == Player then return end
        local head = char:FindFirstChild("Head")
        local hum = char:FindFirstChildOfClass("Humanoid")
        if not head or not hum then return end

        if head:FindFirstChild("PablexNameHP") then head.PablexNameHP:Destroy() end

        local bill = Instance.new("BillboardGui")
        bill.Name = "PablexNameHP"
        bill.Adornee = head
        bill.Size = UDim2.new(0, 160, 0, 35)
        bill.StudsOffset = Vector3.new(0, 2.8, 0)
        bill.AlwaysOnTop = true
        bill.Parent = head

        local nameLabel = Instance.new("TextLabel", bill)
        nameLabel.Size = UDim2.new(1,0,0,16)
        nameLabel.BackgroundTransparency = 1
        nameLabel.Text = plr.DisplayName ~= plr.Name and (plr.DisplayName.." (@ "..plr.Name..")") or plr.Name
        nameLabel.TextColor3 = Color3.new(1,1,1)
        nameLabel.TextStrokeTransparency = 0
        nameLabel.Font = Enum.Font.SourceSansBold
        nameLabel.TextSize = 14

        local hpBg = Instance.new("Frame", bill)
        hpBg.Size = UDim2.new(1,-6,0,8)
        hpBg.Position = UDim2.new(0,3,0,18)
        hpBg.BackgroundColor3 = Color3.new(0,0,0)
        Instance.new("UICorner", hpBg).CornerRadius = UDim.new(0,3)

        local hpFill = Instance.new("Frame", hpBg)
        hpFill.Size = UDim2.new(1,0,1,0)
        hpFill.BackgroundColor3 = Color3.fromRGB(0, 255, 0) -- VERT FIXE
        Instance.new("UICorner", hpFill).CornerRadius = UDim.new(0,3)

        local hpText = Instance.new("TextLabel", hpBg)
        hpText.Size = UDim2.new(1,0,1,0)
        hpText.BackgroundTransparency = 1
        hpText.TextColor3 = Color3.new(1,1,1)
        hpText.TextStrokeTransparency = 0
        hpText.Font = Enum.Font.SourceSans
        hpText.TextSize = 10

        local function updateHP()
            local ratio = math.clamp(hum.Health / hum.MaxHealth, 0, 1)
            hpFill.Size = UDim2.new(ratio, 0, 1, 0)
            hpText.Text = math.floor(hum.Health) .. "/" .. hum.MaxHealth
        end
        hum.HealthChanged:Connect(updateHP)
        updateHP()
    end

    local function removeNameESP(char)
        if char and char:FindFirstChild("Head") then
            local esp = char.Head:FindFirstChild("PablexNameHP")
            if esp then esp:Destroy() end
        end
    end

    local function createHighlight(char)
        if char and not char:FindFirstChild("PablexHighlight") then
            local hl = Instance.new("Highlight")
            hl.Name = "PablexHighlight"
            hl.OutlineColor = Color3.fromRGB(255,0,0)
            hl.OutlineTransparency = 0
            hl.FillTransparency = 1
            hl.Parent = char
        end
    end

    local function removeHighlight(char)
        if char then
            local hl = char:FindFirstChild("PablexHighlight")
            if hl then hl:Destroy() end
        end
    end

    -- Gestion des joueurs
    local function onCharacterAdded(char)
        task.wait(0.2)
        if espEnabled then
            createNameESP(char)
            createHighlight(char)
        end
    end

    local function setupPlayer(plr)
        if plr == Player then return end
        plr.CharacterAdded:Connect(onCharacterAdded)
        plr.CharacterRemoving:Connect(function(c) removeNameESP(c) removeHighlight(c) end)
        if plr.Character then onCharacterAdded(plr.Character) end
    end

    for _, p in Players:GetPlayers() do setupPlayer(p) end
    Players.PlayerAdded:Connect(setupPlayer)

    -- Toggle ESP
    ESPToggle.MouseButton1Click:Connect(function()
        espEnabled = not espEnabled
        ESPToggle.Text = "ESP: "..(espEnabled and "ON" or "OFF")
        for _, p in Players:GetPlayers() do
            if p ~= Player and p.Character then
                if espEnabled then
                    createNameESP(p.Character)
                    createHighlight(p.Character)
                else
                    removeNameESP(p.Character)
                    removeHighlight(p.Character)
                end
            end
        end
    end)

    -- Aimbot avec WALLCHECK + FOV FIXE
    local function getClosest()
        local closest, shortest = nil, FOVRadius
        local center = Camera.ViewportSize / 2

        for _, plr in Players:GetPlayers() do
            if plr ~= Player and plr.Character and plr.Character:FindFirstChild(AimPart) then
                local part = plr.Character[AimPart]
                local pos, onScreen = Camera:WorldToViewportPoint(part.Position)
                if onScreen and isVisible(part) then
                    local dist = (Vector2.new(pos.X, pos.Y) - center).Magnitude
                    if dist < shortest then
                        shortest = dist
                        closest = part
                    end
                end
            end
        end
        return closest
    end

    RunService.RenderStepped:Connect(function()
        FOVCircle.Position = Camera.ViewportSize / 2  -- FOV FIXE AU CENTRE
        FOVCircle.Radius = FOVRadius
        FOVCircle.Visible = AimbotOn

        if AimbotOn then
            local target = getClosest()
            if target then
                Camera.CFrame = Camera.CFrame:Lerp(CFrame.new(Camera.CFrame.Position, target.Position), 0.25)
            end
        end
    end)

    AimbotToggle.MouseButton1Click:Connect(function()
        AimbotOn = not AimbotOn
        AimbotToggle.Text = "Aimbot: "..(AimbotOn and "ON" or "OFF")
    end)

    FOVSlider.FocusLost:Connect(function(enter)
        if enter then
            local n = tonumber(FOVSlider.Text:match("%d+"))
            if n and n >= 20 and n <= 300 then
                FOVRadius = n
                FOVSlider.Text = "FOV: "..n
            end
        end
    end)

    -- Toggle GUI + Drag
    local open = false
    ToggleButton.MouseButton1Click:Connect(function()
        open = not open
        MainFrame.Visible = open
        ToggleButton.Text = open and "Close" or "Open"
    end)

    local function makeDraggable(gui, drag)
        local dragging, startPos, startInput
        drag.InputBegan:Connect(function(i)
            if i.UserInputType == Enum.UserInputType.MouseButton1 or i.UserInputType == Enum.UserInputType.Touch then
                dragging = true
                startPos = gui.Position
                startInput = i.Position
            end
        end)
        drag.InputChanged:Connect(function(i)
            if dragging and (i.UserInputType == Enum.UserInputType.MouseMovement or i.UserInputType == Enum.UserInputType.Touch) then
                local delta = i.Position - startInput
                gui.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
            end
        end)
        UserInputService.InputEnded:Connect(function(i)
            if i.UserInputType == Enum.UserInputType.MouseButton1 or i.UserInputType == Enum.UserInputType.Touch then
                dragging = false
            end
        end)
    end

    makeDraggable(MainFrame, MainDrag)
    makeDraggable(ToggleButton, ToggleDrag)

    print("Pablex77 Hub chargé - ANOUAR IS THE KING")
end
