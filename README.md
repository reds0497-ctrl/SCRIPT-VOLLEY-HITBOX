-- LocalScript → coloque em StarterPlayerScripts
local UserInputService = game:GetService("UserInputService")
local ball = workspace:WaitForChild("Ball") 

local function aumentarHitbox(25)
    local hitbox = ball:FindFirstChild("Hitbox")
    if not hitbox then
        hitbox = Instance.new("Part", ball)
        hitbox.Name = "Hitbox"
        hitbox.Transparency = 0.5
        hitbox.CanCollide = true
        hitbox.Anchored = false
        hitbox.Massless = true
    end
    hitbox.Size = Vector3.new(6, 6, 6)          
    print("Hitbox aumentada!")
end

UserInputService.InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.K then
        aumentarHitbox(25)
    end
end)

-- aumentarHitbox(30)
