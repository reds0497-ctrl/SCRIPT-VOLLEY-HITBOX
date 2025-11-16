-- LocalScript – coloque em StarterPlayerScripts (ou onde preferir)

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")

local player = Players.LocalPlayer
local ball = workspace:WaitForChild("Ball")          -- nome da bola no seu mapa
local hitboxSize = Vector3.new(6, 6, 6)              -- tamanho que você quer

local function criarHitbox()
    if not ball then return end

    -- procura ou cria a parte que será a hitbox
    local hitbox = ball:FindFirstChild("Hitbox")
    if not hitbox then
        hitbox = Instance.new("Part", ball)
        hitbox.Name = "Hitbox"
        hitbox.Transparency = 0.5
        hitbox.CanCollide = true
        hitbox.Anchored = false
        hitbox.Massless = true
    end

    hitbox.Size = hitboxSize
end

-- Exemplo: ativa ao pressionar a tecla "E"
UserInputService.InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.E then
        criarHitbox()
    end
end)

-- Se quiser que a hitbox já venha aumentada ao entrar no jogo:
-- criarHitbox()
