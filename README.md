local Players = game:GetService("Players")
local player = Players.LocalPlayer
local teleportButton = Instance.new("TextButton")
teleportButton.Text = "Teleport to Chests"
teleportButton.Size = UDim2.new(0, 200, 0, 50)
teleportButton.Position = UDim2.new(0.5, -100, 0.5, -25)
teleportButton.Parent = player.PlayerGui.ScreenGui

local function teleportToChests()
    local chests = workspace:FindFirstChild("Chests")
    if chests then
        for _, chest in pairs(chests:GetChildren()) do
            player.Character:MoveTo(chest.Position)
            wait(1) -- Aguarde um segundo antes de teleportar para o próximo baú
        end
    else
        warn("No chests found in the workspace.")
    end
end

teleportButton.MouseButton1Click:Connect(teleportToChests)
