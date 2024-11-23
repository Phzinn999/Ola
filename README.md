local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local ESPButton = Instance.new("TextButton")
local ScamButton = Instance.new("TextButton")
local FreezeButton = Instance.new("TextButton")

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.new(0.5, 0.5, 0.5)
Frame.Position = UDim2.new(0.5, -100, 0.5, -50)
Frame.Size = UDim2.new(0, 200, 0, 100)

ESPButton.Parent = Frame
ESPButton.Text = "Ativar/Desativar ESP"
ESPButton.Size = UDim2.new(1, 0, 0.3, 0)
ESPButton.Position = UDim2.new(0, 0, 0, 0)

ScamButton.Parent = Frame
ScamButton.Text = "Ativar/Desativar Scam"
ScamButton.Size = UDim2.new(1, 0, 0.3, 0)
ScamButton.Position = UDim2.new(0, 0, 0.35, 0)

FreezeButton.Parent = Frame
FreezeButton.Text = "Ativar/Desativar Freeze"
FreezeButton.Size = UDim2.new(1, 0, 0.3, 0)
FreezeButton.Position = UDim2.new(0, 0, 0.7, 0)

local ESPEnabled = false
ESPButton.MouseButton1Click:Connect(function()
    ESPEnabled = not ESPEnabled
    if ESPEnabled then
        for _, player in pairs(game.Players:GetPlayers()) do
            if player ~= game.Players.LocalPlayer and player.Character then
                createESP(player)
            end
        end
    else
        for _, highlight in pairs(game.Workspace:GetDescendants()) do
            if highlight:IsA("Highlight") then
                highlight:Destroy()
            end
        end
    end
end)

local ScamEnabled = false
ScamButton.MouseButton1Click:Connect(function()
    ScamEnabled = not ScamEnabled
    if ScamEnabled then
        local targetPlayer = game.Players:FindFirstChild("NomeDoJogadorAlvo")
        if targetPlayer then
            tradeScam(targetPlayer)
        end
    end
end)

local FreezeEnabled = false
FreezeButton.MouseButton1Click:Connect(function()
    FreezeEnabled = not FreezeEnabled
    if FreezeEnabled then
        local targetPlayer = game.Players:FindFirstChild("NomeDoJogadorAlvo")
        if targetPlayer then
            tradeFreeze(targetPlayer)
        end
    end
end)
